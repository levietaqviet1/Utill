Các Utill có thể cần đến
<!-- Table of Contents -->
# :notebook_with_decorative_cover: Table of Contents
- [Dành cho Java](#Dành-cho-Java)
- [Dành cho C#](#Dành-cho-C#)

## Dành cho Java

- [Quay về Menu](#notebook_with_decorative_cover-Table-of-Contents)
 
- 1. ScannerUltis 

  ```java

package com.vti.ultis;

import java.text.SimpleDateFormat;
import java.time.LocalDate;
import java.util.Scanner;

public class ScannerUltis {
	private static Scanner sc = new Scanner(System.in);

	public static int inputInt() {
		while (true) {
			try {
				return Integer.parseInt(sc.next().trim());
			} catch (Exception e) {
				System.err.println("Nhập lại:");
			}
		}
	}

	public static int inputIntPositive() {
		while (true) {
			try {
				int intPositive = Integer.parseInt(sc.next());
				if (intPositive >= 0) {
					return intPositive;
				} else {
					System.err.println("Nhập lại:");
				}

			} catch (Exception e) {
				System.err.println("Nhập lại:");
			}

		}
	}

	public static Float inputFloat() {
		while (true) {
			try {
				return Float.parseFloat(sc.next());
			} catch (Exception e) {
				System.err.println("Nhập lại:");
			}
		}
	}

	public static Double inputDouble() {
		while (true) {
			try {
				return Double.parseDouble(sc.next());
			} catch (Exception e) {
				System.err.println("Nhập lại:");
			}
		}
	}

	public static String inputString() {
		while (true) {
			String string = sc.next().trim();
			if (!string.isEmpty()) {
				return string;
			} else {
				System.err.println("Nhập lại:");
			}
		}
	}

	public static LocalDate inputLocalDate() {
		System.out.println("Nhập theo định dạng yyyy-MM-dd");
		SimpleDateFormat format = new SimpleDateFormat("yyyy-MM-dd");
		while (true) {
			String localdate = sc.next().trim();
			try {
				if (format.parse(localdate) != null) {
					LocalDate lc = LocalDate.parse(localdate);
					return lc;
				}
			} catch (Exception e) {
				System.err.println("Nhập lại:");
			}

		}
	}

	public static String inputEmail() {
		while (true) {
			String email = ScannerUltis.inputString();
			if (email == null || !email.contains("@")) {
				System.out.print("Nhập lại: ");
			} else {
				return email;
			}
		}
	}

	public static int inputFunction(int a, int b, String errorMessage) {
		while (true) {
			int number = ScannerUltis.inputInt();
			if (number >= a && number <= b) {
				return number;
			} else {
				System.err.println(errorMessage);
			}
		}
	}

	public static String inputPassword() {
		while (true) {
			String password = ScannerUltis.inputString();
			if (password.length() < 6 || password.length() > 12) {
				System.out.print("Nhập lại: ");
				continue;
			}

			boolean hasAtLeast1Character = false;

			for (int i = 0; i < password.length(); i++) {
				if (Character.isUpperCase(password.charAt(i)) == true) {
					hasAtLeast1Character = true;
					break;
				}
			}
			if (hasAtLeast1Character == true) {
				return password;
			} else {
				System.out.print("Mời bạn nhập lại password: ");
			}
		}
	}

	public static String inputPhoneNumber() {
		while (true) {
			String number = ScannerUltis.inputString();
			if (number.length() > 12 || number.length() < 9) {
				System.out.println("Nhập lại");
				continue;
			}

			if (number.charAt(0) != '0') {
				System.out.println("Nhập lại");
				continue;
			}

			boolean isNumber = true;

			for (int i = 0; i < number.length(); i++) {
				if (Character.isDigit(number.charAt(i)) == false) {
					isNumber = false;
					break;
				}
			}
			if (isNumber == true) {
				return number;
			} else {
				System.out.print("Nhập lại: ");
			}

		}
	}

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
