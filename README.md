Các Utill có thể cần đến
<!-- Table of Contents -->
# :notebook_with_decorative_cover: Table of Contents
- [Dành cho Java](#Dành-cho-Java)
- [Dành cho C#](#Dành-cho-C#)

## Dành cho Java

- [Quay về Menu](#notebook_with_decorative_cover-Table-of-Contents)

- 1.Validate

- 2. Hàm Random

  ```java
      public String genCode(int size){ 
        // chose a Character random from this String
        String AlphaNumericString = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
                + "0123456789"
                + "abcdefghijklmnopqrstuvxyz";
        // create StringBuffer size of AlphaNumericString
        StringBuilder sb = new StringBuilder(size);

        for (int i = 0; i < size; i++) {

            // generate a random number between
            // 0 to AlphaNumericString variable length
            int index
                    = (int)(AlphaNumericString.length()
                    * Math.random());

            // add Character one by one in end of sb
            sb.append(AlphaNumericString
                    .charAt(index));
        }
        return sb.toString();
    }
   ```
## Dành cho C#
- 1.Validate
- 2.Hàm nhập giá trị

```C#
public static int GetInt(string mess)
    {
        int a = 0;
        try
        {
            Console.Write(mess);
            a = int.Parse(Console.ReadLine()); // dùng Console.ReadLine() để nhập chữ sau đó dùng int.Parse để ép kiểu sang int
        }
        catch (Exception)
        {

            return GetInt(mess); // dùng đệ quy
        }
        return a;
    }
```
    
```C#
    public static int GetPositiveInteger(string message)
    {
        int input = -1;
        do
        {
            try
            {
                input = int.Parse(InputString("Input n"));
                if (input < 1)
                {
                    throw new Exception();
                }

                return input;
            }
            catch (Exception)
            {
            }

        } while (input == -1);
        return input;
    }
    public static string InputString(string message)
    {
        Console.Write(message);
        return Console.ReadLine().Trim(); // xóa khoảng trắng thừa đầu và cuỗi chuỗi
    }
```
