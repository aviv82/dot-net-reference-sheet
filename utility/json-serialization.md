# json serializer

```c#
using Newtonsoft.Json;

namespace image_resizer.helpers
{
    public static class JSONHelper
    {
        public static string MessageDTOToMessage(MessageDTO dto)
        {
            string messageToReturn = JsonConvert.SerializeObject(dto);
            return messageToReturn;
        }

        public static MessageDTO MessageToMessageDTO(string message)
        {
            MessageDTO messageDTOToReturn = JsonConvert.DeserializeObject<MessageDTO>(message);
            return messageDTOToReturn;
        }
    }
}
```
