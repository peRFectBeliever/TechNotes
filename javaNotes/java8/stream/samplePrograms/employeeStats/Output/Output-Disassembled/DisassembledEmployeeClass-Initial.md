# Compiling without the library reference of Lombok (Project Lombok)

```
C:\rags\TechNotes\javaNotes\java8\stream\samplePrograms\employeeStats (master)
� javac Employee.java
Employee.java:3: error: package lombok does not exist
import lombok.Data;
             ^
Employee.java:5: error: cannot find symbol
@Data
 ^
  symbol: class Data
2 errors

C:\rags\TechNotes\javaNotes\java8\stream\samplePrograms\employeeStats (master)
�
```

# Compiling with the library reference
```
C:\rags\TechNotes\javaNotes\java8\stream\samplePrograms\employeeStats (master)
� javac Employee.java -cp C:\commonj2eelibs\lombok-1.18.12.jar

C:\rags\TechNotes\javaNotes\java8\stream\samplePrograms\employeeStats (master)
� ls -ltrh
total 6.0K
-rw-r--r-- 1 raghs 197610  163 Mar 24 08:18 Employee.java
-rw-r--r-- 1 raghs 197610  424 Mar 24 08:21 ConsoleOutput.md
-rw-r--r-- 1 raghs 197610 1.7K Mar 24 08:21 Employee.class

C:\rags\TechNotes\javaNotes\java8\stream\samplePrograms\employeeStats (master)
�
```

# Disassembling the code generated by Project Lombok (the .class file)

```
C:\rags\TechNotes\javaNotes\java8\stream\samplePrograms\employeeStats (master)
� javap -c Employee.class

Compiled from "Employee.java"
public class Employee {
  public Employee();
    Code:
       0: aload_0
       1: invokespecial #1                  // Method java/lang/Object."<init>":()V
       4: return

  public java.lang.String getName();
    Code:
       0: aload_0
       1: getfield      #7                  // Field name:Ljava/lang/String;
       4: areturn

  public int getAge();
    Code:
       0: aload_0
       1: getfield      #13                 // Field age:I
       4: ireturn

  public char getGender();
    Code:
       0: aload_0
       1: getfield      #17                 // Field gender:C
       4: ireturn

  public void setName(java.lang.String);
    Code:
       0: aload_0
       1: aload_1
       2: putfield      #7                  // Field name:Ljava/lang/String;
       5: return

  public void setAge(int);
    Code:
       0: aload_0
       1: iload_1
       2: putfield      #13                 // Field age:I
       5: return

  public void setGender(char);
    Code:
       0: aload_0
       1: iload_1
       2: putfield      #17                 // Field gender:C
       5: return

  public boolean equals(java.lang.Object);
    Code:
       0: aload_1
       1: aload_0
       2: if_acmpne     7
       5: iconst_1
       6: ireturn
       7: aload_1
       8: instanceof    #8                  // class Employee
      11: ifne          16
      14: iconst_0
      15: ireturn
      16: aload_1
      17: checkcast     #8                  // class Employee
      20: astore_2
      21: aload_2
      22: aload_0
      23: invokevirtual #21                 // Method canEqual:(Ljava/lang/Object;)Z
      26: ifne          31
      29: iconst_0
      30: ireturn
      31: aload_0
      32: invokevirtual #25                 // Method getName:()Ljava/lang/String;
      35: astore_3
      36: aload_2
      37: invokevirtual #25                 // Method getName:()Ljava/lang/String;
      40: astore        4
      42: aload_3
      43: ifnonnull     54
      46: aload         4
      48: ifnull        65
      51: goto          63
      54: aload_3
      55: aload         4
      57: invokevirtual #29                 // Method java/lang/Object.equals:(Ljava/lang/Object;)Z
      60: ifne          65
      63: iconst_0
      64: ireturn
      65: aload_0
      66: invokevirtual #32                 // Method getAge:()I
      69: aload_2
      70: invokevirtual #32                 // Method getAge:()I
      73: if_icmpeq     78
      76: iconst_0
      77: ireturn
      78: aload_0
      79: invokevirtual #36                 // Method getGender:()C
      82: aload_2
      83: invokevirtual #36                 // Method getGender:()C
      86: if_icmpeq     91
      89: iconst_0
      90: ireturn
      91: iconst_1
      92: ireturn

  protected boolean canEqual(java.lang.Object);
    Code:
       0: aload_1
       1: instanceof    #8                  // class Employee
       4: ireturn

  public int hashCode();
    Code:
       0: iconst_1
       1: istore_1
       2: aload_0
       3: invokevirtual #25                 // Method getName:()Ljava/lang/String;
       6: astore_2
       7: iload_1
       8: bipush        59
      10: imul
      11: aload_2
      12: ifnonnull     20
      15: bipush        43
      17: goto          24
      20: aload_2
      21: invokevirtual #40                 // Method java/lang/Object.hashCode:()I
      24: iadd
      25: istore_1
      26: iload_1
      27: bipush        59
      29: imul
      30: aload_0
      31: invokevirtual #32                 // Method getAge:()I
      34: iadd
      35: istore_1
      36: iload_1
      37: bipush        59
      39: imul
      40: aload_0
      41: invokevirtual #36                 // Method getGender:()C
      44: iadd
      45: istore_1
      46: iload_1
      47: ireturn

  public java.lang.String toString();
    Code:
       0: aload_0
       1: invokevirtual #25                 // Method getName:()Ljava/lang/String;
       4: aload_0
       5: invokevirtual #32                 // Method getAge:()I
       8: aload_0
       9: invokevirtual #36                 // Method getGender:()C
      12: invokedynamic #43,  0             // InvokeDynamic #0:makeConcatWithConstants:(Ljava/lang/String;IC)Ljava/lang/String;
      17: areturn
}
```