# LevelUp.Serializer.ProtobufNet

Feature
* Let LevelUp.Serializer support ProtobufNet


Example
```C#
using System;
using LevelUp.Serializer;
using LevelUp.Serializer.ProtobufNet;
using System.Runtime.Serialization;

namespace ConsoleApplication46
{
    [DataContract]
    public class Person
    {
        [DataMember(Order = 1)]
        public string Name { get; set; }
    }

    class Program
    {
        static void Main(string[] args)
        {
            var larry = new Person()
            {
                Name = "Larry Nung"
            };

            var serializer = new ProtobufSerializer();
            var binary = serializer.SerializeToText(larry);

            Console.WriteLine(binary);
            Serializer.RegisterSerializer(SerializerType.Binary, typeof(ProtobufSerializer));
            binary = Serializer.SerializeToText(larry, SerializerType.Binary);

            Console.WriteLine(binary);
            

            larry = Serializer.DeSerializeFromText<Person>(binary, SerializerType.Binary);

            Console.WriteLine(larry.Name);
        }
    }
}
```

Link
----
* [NuGet Gallery | LevelUp.Serializer.ProtobufNet](https://www.nuget.org/packages/LevelUp.Serializer.ProtobufNet/)
