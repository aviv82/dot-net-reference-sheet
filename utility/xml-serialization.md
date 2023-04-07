# xml serialization

## serializer class

```c#
using System;
using System.Xml.Serialization;

namespace book_mark_library.logic.classes
{
    public class XMLSerializer
    {

        public static string SerializeToXml<T>(T obj)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(T));
            StringWriter writer = new StringWriter();
            serializer.Serialize(writer, obj);
            return writer.ToString();
        }

        public static T DeserializeFromXml<T>(string xml)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(T));
            StringReader reader = new StringReader(xml);
            return (T)serializer.Deserialize(reader);
        }
    }
}

```
