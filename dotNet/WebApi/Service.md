# Service

Let the controller make the thing that is supposed that controller do.

the idea of a service is to fulfill the principle of high cohesion where the class has only one responsability, controller only returns to the user messages like Ok or the result of the process on the example of the persons api controller should not create and generate a random person, to do that controller calls another class who is responsible to make that.

Basically Service is a class with a set of functionalities that the controller needs to operate on the user

```cs
using PersonsApi.Models;
using System.Collections.Generic;
namespace PersonsApi.Service
{
    public static class PersonService
    {
        private static int PersonIdSeed = 1000;

        internal static List<Person> Persons { get; }

        static PersonService()
        {
            var person = Utility.generatePersonPropierties();
            person.Number = PersonIdSeed++;
            Persons = new List<Person>
            {person};
        }

        public static List<Person> GetAllPersons() => Persons;

        public static Person? FindPersonById(int id) =>
            Persons.Find(value => value.Number.Equals(id));
        
        public static void Add(Person person)
        {
            person.Number = PersonIdSeed++;
            Persons.Add(person);
        }

        public static Person GenerateRandomPerson()
        {
            var person = Utility.generatePersonPropierties();
            person.Number = PersonIdSeed++;
            Persons.Add(person);
            return person;
        }

        public static List<Person> GenerateMultiplePersons(int quantity)
        {
            List<Person> personsGroup = new List<Person>();
            for (int i = 0; i < quantity; i++)
            {
                personsGroup.Add(PersonService.GenerateRandomPerson());
            }
            Persons.AddRange(personsGroup);
            return personsGroup;
        }

        public static void Delete(int id)
        {
            var person = FindPersonById(id);
            if(person is null)
                return;
            Persons.Remove(person);
        }

        public static string GetPersons()
        {
            var personsData = "";
            foreach (var data in Persons)
            {
                personsData += data.GetStringValues();
            }
            return personsData;
        }
    }
}
```