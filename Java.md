# JAVA 筆記

`Note` `2025.02.28`

 - Start: [time=Wed, May 28, 2025 1:50 PM]
 - Last Update: [time=Fri, Oct 10, 2025 1:13 PM]


### 開發環境與工具

- 線上編譯器：[OneCompiler](https://onecompiler.com/java/)
- 本地環境：JDK 安裝、IDE（IntelliJ、Eclipse）
- CLI 工具：`javac`, `java`, `jar`


## 資料型別與變數宣告
Java 是強型別語言，變數必須先宣告型別才能使用。  

### 原始型別（Primitive Types）
- `int`、`long`、`float`、`double` → 數值  
- `char` → 單一字元  
- `boolean` → `true` / `false`  

```java
int age = 25;
double pi = 3.14159;
char grade = 'A';
boolean isJavaFun = true;
```

### 參考型別（Reference Types）
- `String`、`Array`、`ArrayList`、`HashMap`、自訂 `class`  
- 儲存的是「物件的記憶體位址」  

```java
String name = "Charlie";
int[] numbers = {1, 2, 3};
```


### 資料型別與變數宣告

在 Java 中，變數必須先宣告型別，才能儲存資料。主要分為兩大類：

#### 原始資料型別（Primitive Data Types）
Java 內建 8 種基本型別，直接儲存值（copy by value）。

| 型別      | 位元組 | 範例值 | 範圍 |
|-----------|--------|--------|------|
| `byte`    | 1      | `127`  | -128 ～ 127 |
| `short`   | 2      | `32000`| -32,768 ～ 32,767 |
| `int`     | 4      | `1000` | -2,147,483,648 ～ 2,147,483,647 |
| `long`    | 8      | `100000L` | -9,223,372,036,854,775,808 ～ 9,223,372,036,854,775,807 |
| `float`   | 4      | `3.14f` | 約 ±3.4E38 |
| `double`  | 8      | `3.14159` | 約 ±1.7E308 |
| `char`    | 2      | `'A'`  | Unicode (0 ~ 65535) |
| `boolean` | 1      | `true` | `true` / `false` |

📌 注意：
- `long` 常數要加 `L`，例如 `long num = 123456789L;`
- `float` 常數要加 `f`，例如 `float pi = 3.14f;`
- `char` 使用單引號 `'A'`，字串則用雙引號 `"Hello"`


#### 參考資料型別（Reference Data Types）
這類型別不直接存值，而是存「記憶體位址的參考」（copy by reference）。

- 常見的有：`String`, `Array`, `ArrayList`, `HashMap`, `Object`
- 使用者自訂的 `class` 也屬於參考型別

```java
// Primitive 範例
int a = 10;
int b = a;   // copy by value
b = 20;
System.out.println(a); // 仍然是 10

// Reference 範例
StringBuilder x = new StringBuilder("Hi");
StringBuilder y = x;   // copy by reference
y.append("!");
System.out.println(x); // 輸出 "Hi!"
```


#### 常數（final）
如果變數值不允許被修改，可以用 `final` 宣告：

```java
final double PI = 3.1415926;
// PI = 3.15; // ❌ 編譯錯誤，因為 final 不能再被修改
```


#### 小結
- **Primitive**：直接存值，複製時互不影響
- **Reference**：存位址，複製時會指向同一物件
- **final**：宣告常數，值不可變


## 控制流程
控制程式執行的邏輯分支與迴圈。

### 語法基礎

- 資料型別與變數宣告
- 控制流程：`if`, `switch`, `for`, `while`
- 陣列與集合：`Array`, `ArrayList`, `HashMap`
- 方法與參數傳遞（值 vs 參考）

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Java!");
    }
}
```

### 條件判斷
#### If
```java
int score = 85;
if (score >= 90) {
    System.out.println("優秀");
} else if (score >= 60) {
    System.out.println("及格");
} else {
    System.out.println("不及格");
}
```

#### Switch
```java
int day = 3;
switch (day) {
    case 1: System.out.println("星期一"); break;
    case 2: System.out.println("星期二"); break;
    case 3: System.out.println("星期三"); break;
    default: System.out.println("其他");
}
```

### 迴圈
```java
// for
for (int i = 0; i < 5; i++) {
    System.out.println("i = " + i);
}

// while
int j = 0;
while (j < 5) {
    System.out.println("j = " + j);
    j++;
}
```


### 陣列與集合
#### 陣列（Array）
固定長度，元素型別一致。
```java
int[] arr = {10, 20, 30};
System.out.println(arr[1]); // 20
```

#### ArrayList
可動態增減元素。
```java
import java.util.ArrayList;

ArrayList<String> list = new ArrayList<>();
list.add("Java");
list.add("Python");
System.out.println(list.get(0)); // Java
```

#### HashMap
鍵值對（Key-Value）結構。
```java
import java.util.HashMap;

HashMap<String, Integer> map = new HashMap<>();
map.put("apple", 3);
map.put("banana", 5);
System.out.println(map.get("apple")); // 3
```


#### 方法與參數傳遞
Java 方法可重複使用程式碼，並支援「值傳遞」與「參考傳遞」。

#### 值傳遞（Primitive）
```java
public static void changeValue(int x) {
    x = 100;
}

public static void main(String[] args) {
    int a = 10;
    changeValue(a);
    System.out.println(a); // 仍然是 10
}
```

#### 參考傳遞（Reference）
```java
public static void changeArray(int[] arr) {
    arr[0] = 99;
}

public static void main(String[] args) {
    int[] nums = {1, 2, 3};
    changeArray(nums);
    System.out.println(nums[0]); // 99
}
```


#### HelloWorld 範例
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Java!");
    }
}
```

說明：  
- `public class HelloWorld` → 定義一個類別  
- `public static void main(String[] args)` → 主程式進入點  
- `System.out.println()` → 輸出文字到終端機  


### 物件導向設計（OOP）

Java 採用 **物件導向程式設計（Object-Oriented Programming, OOP）**，核心概念包含：  

- 類別與物件
- 封裝、繼承、多型
- `interface` vs `abstract class`

```java
interface Sorter {
    void sort(int[] arr);
}

class BubbleSorter implements Sorter {
    public void sort(int[] arr) {
        // 泡泡排序邏輯
    }
}
```


#### 類別與物件（Class & Object）
- **類別（Class）**：定義資料結構與行為的「藍圖」  
- **物件（Object）**：依照類別建立的實體  

```java
class Student {
    String name;
    int age;

    void study() {
        System.out.println(name + " 正在學習 Java");
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student(); // 建立物件
        s1.name = "Hsieh";
        s1.age = 25;
        s1.study(); // 輸出：Hsieh 正在學習 Java
    }
}
```


#### 封裝（Encapsulation）
- 將資料與方法「包裝」在類別中，並透過 **存取修飾子** 控制可見性  
- 常見修飾子：`public`, `private`, `protected`  
- 好處：保護資料、避免外部隨意修改  

```java
class Account {
    private int balance = 1000;

    public int getBalance() {
        return balance;
    }

    public void deposit(int amount) {
        if (amount > 0) balance += amount;
    }
}
```


#### 繼承（Inheritance）
- 子類別可以繼承父類別的屬性與方法  
- 減少重複程式碼，提升可維護性  

```java
class Animal {
    void eat() {
        System.out.println("正在吃東西");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("汪汪！");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.eat();  // 繼承自 Animal
        d.bark(); // 自己的方法
    }
}
```


#### 多型（Polymorphism）
- 相同的方法呼叫，依物件型別不同而有不同表現  
- 透過 **方法覆寫（Override）** 或 **介面實作** 達成  

```java
class Animal {
    void speak() {
        System.out.println("動物發出聲音");
    }
}

class Dog extends Animal {
    @Override
    void speak() {
        System.out.println("汪汪！");
    }
}

class Cat extends Animal {
    @Override
    void speak() {
        System.out.println("喵喵！");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a1 = new Dog();
        Animal a2 = new Cat();
        a1.speak(); // 汪汪！
        a2.speak(); // 喵喵！
    }
}
```


#### `interface` vs `abstract class`
- **interface（介面）**：定義「行為規範」，不能有實作（Java 8+ 可有 `default` 方法）  
- **abstract class（抽象類別）**：可包含「部分實作」與「抽象方法」  

| 特性 | interface | abstract class |
|------|-----------|----------------|
| 多重繼承 | ✅ 可實作多個 | ❌ 只能繼承一個 |
| 成員變數 | 預設 `public static final` | 可有一般屬性 |
| 方法 | 抽象方法（Java 8+ 可有 `default`） | 可有抽象與具體方法 |
| 使用場景 | 定義規範（行為契約） | 提供部分共用邏輯 |

```java
interface Sorter {
    void sort(int[] arr);
}

abstract class AbstractSorter {
    abstract void sort(int[] arr);

    void printArray(int[] arr) {
        for (int n : arr) System.out.print(n + " ");
        System.out.println();
    }
}

class BubbleSorter extends AbstractSorter implements Sorter {
    @Override
    public void sort(int[] arr) {
        // 泡泡排序邏輯
    }
}
```


#### 小結
- **類別與物件**：藍圖與實體  
- **封裝**：保護資料，提供介面  
- **繼承**：重用程式碼，建立階層  
- **多型**：相同介面，不同行為  
- **interface vs abstract class**：規範 vs 部分實作  


## 資料結構與演算法
### 演算法與資料結構

- 排序法：泡泡排序、選擇排序、快速排序
- 搜尋法：線性搜尋、二分搜尋
- 樹結構：Binary Tree 範例與遍歷（Pre/In/Post）

```java
public static void bubbleSort(int[] arr) {
    int n = arr.length;
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}
```

#### 泡泡排序

```java=
import java.util.Arrays;

public class BubbleSort {

    public static void main(String[] args) {
        int[] arr = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};
        System.out.println("原始陣列: " + Arrays.toString(arr));

        bubbleSort(arr);

        System.out.println("排序後的陣列: " + Arrays.toString(arr));

        // 測試其他案例
        int[] arr2 = {5, 1, 4, 2, 8};
        System.out.println("\n原始陣列 (arr2): " + Arrays.toString(arr2));
        bubbleSort(arr2);
        System.out.println("排序後的陣列 (arr2): " + Arrays.toString(arr2));

        int[] arr3 = {}; // 空陣列
        System.out.println("\n原始陣列 (arr3): " + Arrays.toString(arr3));
        bubbleSort(arr3);
        System.out.println("排序後的陣列 (arr3): " + Arrays.toString(arr3));

        int[] arr4 = {7}; // 單一元素陣列
        System.out.println("\n原始陣列 (arr4): " + Arrays.toString(arr4));
        bubbleSort(arr4);
        System.out.println("排序後的陣列 (arr4): " + Arrays.toString(arr4));
    }

    /**
     * 使用泡泡排序法對整數陣列進行排序。
     *
     * @param arr 要排序的整數陣列。
     */
    public static void bubbleSort(int[] arr) {
        int n = arr.length;
        boolean swapped; // 判斷是否發生交換，若一輪沒有交換表示已排序完成

        for (int i = 0; i < n - 1; i++) {
            swapped = false;
            // 每一輪會將最大的元素「浮」到最右邊已排序的位置
            // 因此內層迴圈的範圍會遞減
            for (int j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    // 交換 arr[j] 和 arr[j+1]
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                    swapped = true;
                }
            }

            // 如果一輪沒有發生任何交換，表示陣列已經排序完成
            if (!swapped) {
                break;
            }
        }
    }
}
```

程式碼解釋：
 * BubbleSort 類別： 包含 main 方法和 bubbleSort 方法。
 * main 方法：
   * 定義了一個整數陣列 arr 作為範例。
   * 列印原始陣列。
   * 呼叫 bubbleSort 方法對陣列進行排序。
   * 列印排序後的陣列。
   * 包含了一些額外的測試案例來驗證程式的"合理"性。
 * bubbleSort(int[] arr) 方法：
   * int n = arr.length;: 取得陣列的長度。
   * boolean swapped;: 這是泡泡排序的一個優化點。如果在一輪內層迴圈中沒有任何元素被交換，表示陣列已經是排序好的，這時就可以提前終止排序，避免不必要的比較。
   * 外層迴圈 for (int i = 0; i < n - 1; i++):
     * 這個迴圈控制排序的「輪數」。對於一個有 n 個元素的陣列，最多需要 n-1 輪才能完成排序。
     * 每一輪都會將一個最大的（或最小的，取決於排序方向）未排序元素移動到其最終的正確位置。
   * 內層迴圈 for (int j = 0; j < n - 1 - i; j++):
     * 這個迴圈負責遍歷未排序的部分，並比較相鄰的元素。
     * n - 1 - i：隨著外層迴圈的進行，右邊的 i 個元素已經排序好，所以內層迴圈的比較範圍會逐漸縮小。
     * if (arr[j] > arr[j + 1]): 如果當前元素 arr[j] 大於下一個元素 arr[j + 1]，則它們的順序不正確，需要進行交換。
     * 交換操作：
       int temp = arr[j];
arr[j] = arr[j + 1];
arr[j + 1] = temp;
swapped = true; // 標記發生了交換

   * 優化：if (!swapped) { break; }: 如果內層迴圈執行完畢後 swapped 仍然是 false，表示這一輪沒有發生任何交換，說明陣列已經完全排序，可以提前結束外層迴圈。
泡泡排序法的特性：
 * 時間複雜度：
   * 最壞情況： O(n^2) (例如，當陣列完全逆序時)。
   * 平均情況： O(n^2)。
   * 最好情況： O(n) (當陣列已經排序好時，因為有優化)。
 * 空間複雜度： O(1) (原地排序，不需額外的大量空間)。
 * 穩定性： 穩定排序演算法（相等元素的相對順序不會改變）。
雖然泡泡排序在實際應用中效率不高，但它是一個很好的入門級排序演算法，有助於理解排序的基本概念。

- [time=Fri, Aug 1, 2025 12:06 AM]


### 泡泡排序法 物件導向

```java=
import java.util.Arrays;

// 定義一個排序器介面
interface Sorter {
    void sort(int[] arr);
}

// 實作泡泡排序的類別
class BubbleSorter implements Sorter {
    @Override
    public void sort(int[] arr) {
        // 為了避免 NullPointerException，先進行 null 值檢查
        if (arr == null || arr.length <= 1) {
            return;
        }

        int n = arr.length;
        boolean swapped;

        for (int i = 0; i < n - 1; i++) {
            swapped = false;
            for (int j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    // 交換元素
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                    swapped = true;
                }
            }
            if (!swapped) {
                break;
            }
        }
    }
}

public class OOPSortingExample {

    public static void main(String[] args) {
        int[] arr = {5, 1, 4, 2, 8};
        System.out.println("原始陣列: " + Arrays.toString(arr));

        // 創建一個 BubbleSorter 物件
        Sorter mySorter = new BubbleSorter();

        // 呼叫物件的方法來進行排序
        mySorter.sort(arr);

        System.out.println("排序後的陣列: " + Arrays.toString(arr));
    }
}
```

```java=
import java.util.Arrays;

// 將資料與行為封裝在一個類別中
class SortableArray {
    private int[] data;

    public SortableArray(int[] arr) {
        // 複製一份陣列，避免外部修改原始陣列
        this.data = Arrays.copyOf(arr, arr.length);
    }

    public void bubbleSort() {
        if (data == null || data.length <= 1) {
            return;
        }

        int n = data.length;
        boolean swapped;

        for (int i = 0; i < n - 1; i++) {
            swapped = false;
            for (int j = 0; j < n - i - 1; j++) {
                if (data[j] > data[j + 1]) {
                    // 交換元素
                    int temp = data[j];
                    data[j] = data[j + 1];
                    data[j + 1] = temp;
                    swapped = true;
                }
            }
            if (!swapped) {
                break;
            }
        }
    }

    public void printArray() {
        System.out.println(Arrays.toString(data));
    }
}

public class OOPSortingExample2 {

    public static void main(String[] args) {
        int[] originalArr = {5, 1, 4, 2, 8};
        System.out.print("原始陣列: ");
        System.out.println(Arrays.toString(originalArr));

        // 創建一個 SortableArray 物件
        SortableArray mySortableArray = new SortableArray(originalArr);

        // 執行排序行為
        mySortableArray.bubbleSort();

        System.out.print("排序後的陣列: ");
        mySortableArray.printArray();
    }
}
```

- [time=Wed, Sep 17, 2025 11:30 AM]


### Binary Tree

```java=
public class BinaryTree {

    // 定義二元樹節點結構
    static class Node {
        int data;
        Node left;
        Node right;

        Node(int data) {
            this.data = data;
            this.left = null;
            this.right = null;
        }
    }

    // 建立新節點
    static Node createNode(int data) {
        return new Node(data);
    }

    // 修改節點資料
    static void modifyNode(Node node, int newData) {
        if (node != null) {
            node.data = newData;
        }
    }

    // 前序遍歷：根 → 左 → 右
    static void preOrderTraversal(Node root) {
        if (root != null) {
            System.out.print(root.data + " ");
            preOrderTraversal(root.left);
            preOrderTraversal(root.right);
        }
    }

    // 中序遍歷：左 → 根 → 右
    static void inOrderTraversal(Node root) {
        if (root != null) {
            inOrderTraversal(root.left);
            System.out.print(root.data + " ");
            inOrderTraversal(root.right);
        }
    }

    // 後序遍歷：左 → 右 → 根
    static void postOrderTraversal(Node root) {
        if (root != null) {
            postOrderTraversal(root.left);
            postOrderTraversal(root.right);
            System.out.print(root.data + " ");
        }
    }

    public static void main(String[] args) {
        // 建立節點並構建樹結構
        Node root = createNode(0);
        root.left = createNode(1);
        root.right = createNode(2);
        root.left.left = createNode(3);
        root.left.right = createNode(4);
        root.right.left = createNode(5);
        root.right.right = createNode(6);
        root.left.left.left = createNode(7);
        root.left.left.right = createNode(8);
        root.left.right.left = createNode(9);

        System.out.print("Pre-order Traversal: ");
        preOrderTraversal(root);
        System.out.println();

        System.out.print("In-order Traversal: ");
        inOrderTraversal(root);
        System.out.println();

        System.out.print("Post-order Traversal: ");
        postOrderTraversal(root);
        System.out.println();
    }
}
```
```
Pre-order Traversal: 0 1 3 7 8 4 9 2 5 6
In-order Traversal: 7 3 8 1 9 4 0 5 2 6
Post-order Traversal: 7 8 3 9 4 1 5 6 2 0
```

- [time=Tue, Sep 16, 2025 3:37 PM]


### 二分搜尋法

```java=
public class SortAndSearch {

    // 泡泡排序法
    public static void bubbleSort(int[] arr) {
        int i = arr.length;

        while (i > 0) {
            int j = 1;
            while (j < i) {
                if (arr[j] < arr[j - 1]) {
                    // 交換 arr[j] 和 arr[j-1]
                    int w = arr[j];
                    arr[j] = arr[j - 1];
                    arr[j - 1] = w;
                }
                j++;
            }
            i--;
        }
    }

    // 二分搜尋法
    public static int binarySearch(int[] arr, int target) {
        int left = 0;
        int right = arr.length - 1;

        System.out.println("搜尋對象: " + target);

        while (left <= right) {
            int moderate = (left + right) / 2;
            System.out.println("取中間數: " + moderate);

            if (arr[moderate] == target) {
                return moderate; // 找到目標
            } else if (arr[moderate] < target) {
                left = moderate + 1;
                System.out.println("往右邊找!");
            } else {
                right = moderate - 1;
                System.out.println("往左邊找!");
            }
        }

        return -1; // 沒找到
    }

    public static void main(String[] args) {
        // 未排序的陣列
        int[] arr = {5, 2, 9, 1, 7, 6, 3, 8, 0, 4};
        int target = 2;

        System.out.print("原始陣列：\t");
        for (int value : arr) {
            System.out.print(value + " ");
        }
        System.out.println();

        // 排序陣列
        bubbleSort(arr);

        System.out.print("排序後的陣列：\t");
        for (int value : arr) {
            System.out.print(value + " ");
        }
        System.out.println();

        // 查找目標值
        int result = binarySearch(arr, target);
        if (result != -1) {
            System.out.printf("找到數值 %d 在索引位置 %d。\n", target, result);
        } else {
            System.out.printf("找不到數值 %d。\n", target);
        }
    }
}
```
```
Output:

原始陣列：	5 2 9 1 7 6 3 8 0 4 
排序後的陣列：	0 1 2 3 4 5 6 7 8 9 
搜尋對象: 2
取中間數: 4
往左邊找!
取中間數: 1
往右邊找!
取中間數: 2
找到數值 2 在索引位置 2。
```

- [time=Tue, Sep 16, 2025 3:51 PM]


### 測試與除錯

- 單元測試：JUnit 基礎
- 例外處理：`try-catch-finally`
- 日誌紀錄：`System.out` vs `Logger`


### 專案結構與模組化

- `package` 使用與命名慣例
- 多檔案專案架構
- Maven/Gradle 基礎（可選）


### 延伸應用（可選模組）

- Java GUI：Swing / JavaFX
- Java Web：Servlet / Spring Boot
- Android 開發（Java 基礎）


#### Acknowledge

* [C筆記](https://hackmd.io/@EIT-/c_)
* [Java SE8 OCAJP專業認證指南](https://www.books.com.tw/products/E050057008?sloc=main)
* [Java SE8 OCPJP進階認證指南](https://www.books.com.tw/products/E050057009?loc=P_br_r0vq68ygz_D_2aabd0_C_2)
* [圖說演算法：使用Java](https://www.books.com.tw/products/0010845577?srsltid=AfmBOorSBSqLayCMDhKlKUbhG0chwU_glufk4z3ZesciogVpXzFTCEqK)