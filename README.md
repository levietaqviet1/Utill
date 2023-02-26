Các Utill có thể cần đến
<!-- Table of Contents -->
# :notebook_with_decorative_cover: Table of Contents
- [Dành cho Java](#Dành-cho-Java)
- [Dành cho C#](#Dành-cho-C#)

## Dành cho Java

- [Quay về Menu](#notebook_with_decorative_cover-Table-of-Contents)
 
1. ScannerUltis 

```java
package ultis;

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

2. FileUltis 

```java

package ultis;

import java.io.File;
import java.nio.file.Files;
import java.util.Arrays;
import java.util.List;

public class FileUltis {
	public static final String FILE_EXISTS = "File is exits!";
	public static final String FILE_NOT_EXISTS = "Error! File Not Exist.";
	public static final String FOLDER_EXISTS = "Folder is exits!";
	public static final String FOLDER_NOT_EXISTS = "Folder is not exits!";
	public static final String PATH_NOT_FOLDER = "Error! Path is not folder.";

	public static final String SOURCE_FILE_NOT_EXISTS = "Source File is not exits!";
	public static final String DESTINATION_FILE_EXISTS = "Destination File is exits!";

	public static final String NEW_FILE_EXISTS = "Error! New File Exist.";
	public static final String CREATE_FILE_SUCCESS = "Create file success!";
	public static final String CREATE_FILE_FAIL = "Create file fail!";
	public static final String DELETE_FILE_SUCCESS = "Delete file success!";
	public static final String DELETE_FILE_FAIL = "Delete file fail!";

	public static boolean isFileExists(String pathFile) {
		return new File(pathFile).exists() ? true : false;
	}

	// Check folder is exists
	public static boolean isFolderExists(String pathFolder) {
		return new File(pathFolder).exists() ? true : false;
	}

	// Create file
	public static void createNewFile(String pathFile) throws Exception {
		if (isFileExists(pathFile)) {
			throw new Exception(FILE_EXISTS);
		}

		boolean result = new File(pathFile).createNewFile();

		System.out.println(result ? CREATE_FILE_SUCCESS : CREATE_FILE_FAIL);
	}

	public static void createNewFile(String path, String fileName) throws Exception {
		String pathFile = path + "//" + fileName;
		createNewFile(pathFile);
	}

	// Delete file
	public static void deleteFile(String pathFile) throws Exception {
		if (!isFileExists(pathFile)) {
			throw new Exception(FILE_NOT_EXISTS);
		}

		boolean result = new File(pathFile).delete();

		System.out.println(result ? DELETE_FILE_SUCCESS : DELETE_FILE_FAIL);
	}

	// Check path is File or Folder
	public static void isFolderOrFile(String pathFile) {
		File file = new File(pathFile);
		if (file.isDirectory()) {
			System.out.println("Đây là 1 Foder");
		} else if (file.isFile()) {
			System.out.println("Đây là 1 file");
		} else {
			System.out.println("Đây không phải đường dãn, cũng không phải file");
		}
	}

	// Check path is Folder
	public static boolean isFolder(String pathFile) {
		File file1 = new File(pathFile);
		return file1.isDirectory();
	}

	// Get all file name of folder
	public static String[] getAllFileName(String path) {

		File file = new File(path);
		if (!isFolder(path)) {
			System.out.println("Đây không phải là đường dẫn!!");
			return null;
		} else {
			return file.list();
		}

	}

	// Copy File
	public static void copyFile(String sourceFile, String destinationPath) throws Exception {

		if (!isFileExists(sourceFile)) {
			throw new Exception(SOURCE_FILE_NOT_EXISTS);
		}

		String[] s = sourceFile.split("/");
		String nameFile = s[s.length - 1];

		String destinationFile = destinationPath + "//" + nameFile;

		if (isFileExists(destinationFile)) {
			throw new Exception(DESTINATION_FILE_EXISTS);
		}

		File source = new File(sourceFile);
		File dest = new File(destinationPath);

		Files.copy(source.toPath(), dest.toPath());
	}

	// Moving file
	public static void moveFile(String sourceFile, String destinationPath) throws Exception {

		if (!isFileExists(sourceFile)) {
			throw new Exception(SOURCE_FILE_NOT_EXISTS);
		}

		File source = new File(sourceFile);
		File dest = new File(destinationPath);
		Files.move(source.toPath(), dest.toPath());
	}

	// Rename File
	public static void renameFile(String pathFile, String newName) throws Exception {

		if (!isFileExists(pathFile)) {
			throw new Exception(FILE_NOT_EXISTS);
		}

		if (isFileExists(newName)) {
			throw new Exception(NEW_FILE_EXISTS);
		}
		File oldFile = new File(pathFile);
		File newFile = new File(newName);
		oldFile.renameTo(newFile);
	}
	
	// Create New Folder
		public static void createNewFolder(String newPathFolder) throws Exception {
			if (isFolderExists(newPathFolder)) {
				throw new Exception(FOLDER_EXISTS);
			}
			new File(newPathFolder).mkdir();
		}
}

```

3. IOManager  

```java
package ultis;

import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.ObjectInputStream;
import java.io.ObjectOutputStream;

public class IOManager {

	private static final String FILE_NOT_EXIST = "Error! File not Exist.";
	private static final String WRITE_FILE_SUCCESS = "Write file success!";
	private static final String READ_FILE_SUCCESS = "Read file success!";

	public static String readFile(String pathFile) throws Exception {
		if (!FileUltis.isFileExists(pathFile)) {
			throw new Exception(FILE_NOT_EXIST);
		}
		byte[] b = new byte[1024];
		FileInputStream in = new FileInputStream(pathFile);
		int length = in.read(b);
		String output = "";
		while (length > -1) {
			String content = new String(b, 0, length);
//			System.out.println(content + "\n " + length);
			output += content;
			length = in.read(b);
		}
		in.close();
		return output;
	}

	public static void writeFile(String pathFile, boolean isContinuing, String content) throws Exception {
		if (!FileUltis.isFileExists(pathFile)) {
			throw new Exception(FILE_NOT_EXIST);
		}
		FileOutputStream out = new FileOutputStream(pathFile, isContinuing);
		out.write(content.getBytes());
		out.close();
		System.out.println(WRITE_FILE_SUCCESS);
	}

	public static void writeObject(Object object, String path, String fileName) throws Exception {
		if (!FileUltis.isFileExists(path)) {
			throw new Exception(FILE_NOT_EXIST);
		}
		System.out.print("File name:");
		fileName = ScannerUltis.inputString();
		path = path + "\\" + fileName;
		FileOutputStream out = new FileOutputStream(path);
		ObjectOutputStream objectOut = new ObjectOutputStream(out);
		objectOut.writeObject(object);
		out.close();
		objectOut.close();
		System.out.println(WRITE_FILE_SUCCESS);
	}

	public static void writeObject(Object object, String path) throws Exception {
		if (!FileUltis.isFileExists(path)) {
			throw new Exception(FILE_NOT_EXIST);
		}
		FileOutputStream out = new FileOutputStream(path);
		ObjectOutputStream objectOut = new ObjectOutputStream(out);
		objectOut.writeObject(object);
		out.close();
		objectOut.close();
		System.out.println(WRITE_FILE_SUCCESS);
	}

	public static Object readObject(String filePath) throws Exception {
		if (!FileUltis.isFileExists(filePath)) {
			throw new Exception(FILE_NOT_EXIST);
		}
		FileInputStream in = null;
		ObjectInputStream objectIn = null;
		try {
			in = new FileInputStream(filePath);
			objectIn = new ObjectInputStream(in);
			System.out.println(READ_FILE_SUCCESS);
			return objectIn.readObject();
		} finally {
			in.close();
			objectIn.close();
		}

	}
}
```

4. Validation

```java
package ultis;

import java.text.*;
import java.util.*;

public class Validation {
    
    static Scanner sc = new Scanner(System.in);
    
    /**
     * Yêu cầu người dùng nhập vào một số nguyên trong khoảng từ min đến max.
     * @param msg
     * @param min
     * @param max
     * @return 
     */
    public static int getInt(String msg, int min, int max) {
        int n;
        do {
            System.out.print(msg);
            try {
                n = Integer.parseInt(sc.nextLine());
                if (min <= n && n <= max) {
                    return n;
                }
                System.err.println("Must from: " + min + " -> " + max);
            } catch (NumberFormatException ex) {
                System.err.println("Wrong format");
            }
        } while (true);
    }
    
    /**
     * Yêu cầu người dùng nhập vào một chuỗi thỏa mãn một điều kiện nhất định
     *
     * @param msg
     * @param pattern
     * @param err
     * @return
     */
    public static String getString(String msg, String pattern, String err) {
        String s;
        do {
            System.out.print(msg);
            s = sc.nextLine().trim();
            if (!s.matches(pattern)) {
                System.err.println(err);
            }
        } while (!s.matches(pattern));
        return s;
    }
    
    // Tạo một đối tượng SimpleDateFormat ở ngoài hàm và sử dụng lại đối tượng đó thay vì tạo mới ở mỗi lần
    private static SimpleDateFormat sdf = new SimpleDateFormat("MM/dd/yyyy");
    
    /**
     * Yêu cầu người dùng nhập vào một ngày theo định dạng MM/dd/yyyy
     *
     * @param msg
     * @return
     */
    public static Date getDate(String msg) {
        sdf.setLenient(false);
        Date d;
        do {
            System.out.print(msg);
            String date = sc.nextLine().trim();
            try {
                d = sdf.parse(date);
            } catch (ParseException ex) {
                System.err.println("Wrong format, must be MM/dd/yyyy");
                d = null;
            }
        } while (d == null);
        return d;
    }
    
}

```


## Dành cho C#
- 1.Validate
- 2.Hàm nhập giá trị

```C#
public class Validation
    {
        private static readonly CultureInfo culture = new CultureInfo("en-US");
        private static readonly DateTimeStyles dateStyle = DateTimeStyles.None;

        /**
        * Yêu cầu người dùng nhập vào một số nguyên trong khoảng từ min đến max.
        * @param msg
        * @param min
        * @param max
        * @return 
        */
        public static int GetInt(string msg, int min, int max)
        {
            int n;
            do
            {
                Console.Write(msg);
                try
                {
                    n = int.Parse(Console.ReadLine());
                    if (min <= n && n <= max)
                    {
                        return n;
                    }
                    Console.Error.WriteLine("Must from: " + min + " -> " + max);
                }
                catch (FormatException)
                {
                    Console.Error.WriteLine("Wrong format");
                }
            } while (true);
        }

        /**
        * Yêu cầu người dùng nhập vào một chuỗi thỏa mãn một điều kiện nhất định
        *
        * @param msg
        * @param pattern
        * @param err
        * @return
        */
        public static string GetString(string msg, string pattern, string err)
        {
            string s;
            bool check;
            do
            {
                Console.Write(msg);
                s = Console.ReadLine().Trim();
                check = !System.Text.RegularExpressions.Regex.IsMatch(s, pattern);
                if (check)
                {
                    Console.Error.WriteLine(err);
                }
            } while (check);
            return s;
        }
        /**
        * Yêu cầu người dùng nhập vào một ngày theo định dạng MM/dd/yyyy
        *
        * @param msg
        * @return
        */
        public static DateTime GetDate(string msg, string format = "MM/dd/yyyy")
        {
            DateTime d;
            do
            {
                Console.Write(msg);
                string date = Console.ReadLine().Trim();
                if (!DateTime.TryParseExact(date, format, culture, dateStyle, out d))
                {
                    Console.Error.WriteLine($"Wrong format, must be {format}");
                    d = DateTime.MinValue;
                }
            } while (d == DateTime.MinValue);
            return d;
        }
    }
```
    
 
