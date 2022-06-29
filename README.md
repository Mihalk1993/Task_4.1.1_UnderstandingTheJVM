# Task_4.1.1_UnderstandingTheJVM
JVM. Memory organization, garbage collectors, VisualVM homework

```java
public class JvmComprehension {
// Система загрузчика классов ClassLoaders загружает класс JvmComprehension в MetaSpace.
// В рамках загрузки класса при инициализации класса также инициализируется статический метод printAll() данного класса.

    public static void main(String[] args) {
// 0) В момент вызова метода создается frame main() в стеке (Stack Memory).

        int i = 1;                           
// 1) В стеке (Stack Memory) во фрейме main() создаётся примитивная переменная "i" типа int, её присвается значение 1.

        Object o = new Object();        
// 2) В куче (Heap) создается объект класса Object, а в стеке (Stack Memory) во фрейме main() создается переменная "o",
//в которую помещается ссылка на этот объект.

        Integer ii = 2;                 
// 3) В куче (Heap) создается объект класса Integer, ему присваевается значение "2", а в стеке (Stack Memory)
//во фрейме main() создается переменная "ii", в которую помещается ссылка на этот объект.

        printAll(o, i, ii);             
// 4) В стеке (Stack Memory) создается frame prinAll();
// Во фрейме prinAll() создается переменная "o", в которую помещается ссылка на объект Object;
// Во фрейме prinAll() создается переменная "ii", в которую помещается ссылка на объект Integer, имеющий значение 2;
// Во фрейме prinAll() создается переменная "i" типа int, её присвается значение 1 (по аналогии с ссылочными переменными).
// Переменные "o", "i" и "ii" из фрейма prinAll() передаются как аргументы в метод prinAll().
// Фрейм prinAll() после выполнения метода prinAll() удаляется из стека (Stack Memory).

        System.out.println("finished"); 
// 7) В стеке (Stack Memory) создается фрейм println(), в него передается ссылка на объект типа String со значением "finished",
// созданный в Куче (Heap).
// Фрейм println() после выполнения метода prinAll() удаляется из стека (Stack Memory).
    }
    
// В процессе работы программы периодически может отрабатывать Garbage Collector, собирая неиспользуемые объекты из кучи (Heap).
    
    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;
// 5) В куче (Heap) создается объект класса Integer, ему присваевается значение "700", а в стеке (Stack Memory)
// во фрейме prinAll() создается переменная "uselessVar", в которую помещается ссылка на этот объект.

        System.out.println(o.toString() + i + ii);
// 6) В стеке (Stack Memory) создается frame println();

// Во фрейме println() создается переменная "o", в которую помещается ссылка на объект Object;
// Во фрейме println() создается переменная "ii", в которую помещается ссылка на объект Integer, имеющий значение 2;
// Во фрейме println() создается переменная "i" типа int, её присвается значение 1 (по аналогии с ссылочными переменными).
// Переменные "o","i" и "ii" из фрейма println() передаются как аргументы в метод println().

// В стеке (Stack Memory) создается frame toString().

// Фрейм toString() после выполнения метода toString() удаляется из стека (Stack Memory).

// Фрейм println() после выполнения метода println() удаляется из стека (Stack Memory).

    }
}
```
