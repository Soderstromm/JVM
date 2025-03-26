# JVM
JVM


public class JvmComprehension { // Загрузка класса через ClassLoader в MetaSpace

    public static void main(String[] args) { //Создаётся фрейм в Stack Memory
        int i = 1;                      // В фрейме main создаётся переменная i
        Object o = new Object();        // В heap создаётся Object, для него создаётся ссылка "o" в фрейме main
        Integer ii = 2;                 // В heap создаётся Integer, для него создаётся ссылка "ii" в фрейме main
        printAll(o, i, ii);             // Создаётся новый фрейм printAll c параметрами o, i, ii, после выполнения фрейм удаляется.
        System.out.println("finished"); // Создаётся новый фрейм System.out.println, в heap создаётся String Pool, в котором хранится "finished", далее ссылка на String Pool передаётся в println()
    }

    private static void printAll(Object o, int i, Integer ii) { // В фрейм printAll копируется значение i и передаются ссылки на o, ii
        Integer uselessVar = 700;                   // В heap создаётся Integer, для него создаётся ссылка "uselessVar" в фрейме printAll
        System.out.println(o.toString() + i + ii);  // Создаётся новый фрейм toString(), в heap создаётся String, для которого создаётся ссылка с результатом метода o.toString(), далее создаётся в heap String, в который передаётся результат o.toString() + i + ii, 
                                                    // далее создаётся фрейм System.out.println в который передадим ссылку на String с результатом o.toString() + i + ii
    }
}
