28-03-2023
11:59
Authors: Tamerlan Khutuev
***
Tags: #stub #patterns 
***
# Интерпретатор

>Для заданного языка определяет представление его грамматики, а также интерпретатор предложений этого языка.
>(Паттерны объектно-ориентированного программирования 2020. GoF)

## Проблема
В некоторых приложениях может возникнуть необходимость интерпретировать и выполнять некоторые команды, заданные в текстовом виде. Например, в математических программах могут быть заданы формулы, которые должны быть интерпретированы и вычислены в результате.

## Решение
Паттерн Интерпретатор предлагает создание объектов для каждого терминала и нетерминала языка, который нужно интерпретировать. Затем эти объекты объединяются в древовидную структуру, которая представляет собой абстрактное синтаксическое дерево (AST) для команд. Интерпретатор проходит по AST и выполняет команды.

## Пример
```java
public interface Expression {
    int interpret();
}

public class NumberExpression implements Expression {
    private int number;

    public NumberExpression(int number) {
        this.number = number;
    }

    public int interpret() {
        return number;
    }
}

public class AdditionExpression implements Expression {
    private Expression left;
    private Expression right;

    public AdditionExpression(Expression left, Expression right) {
        this.left = left;
        this.right = right;
    }

    public int interpret() {
        return left.interpret() + right.interpret();
    }
}

public class MultiplicationExpression implements Expression {
    private Expression left;
    private Expression right;

    public MultiplicationExpression(Expression left, Expression right) {
        this.left = left;
        this.right = right;
    }

    public int interpret() {
        return left.interpret() * right.interpret();
    }
}

public class Interpreter {
    public static void main(String[] args) {
        Expression expression = new AdditionExpression(
                new NumberExpression(2),
                new MultiplicationExpression(
                        new NumberExpression(3),
                        new NumberExpression(4)
                )
        );
        System.out.println(expression.interpret()); // Output: 14
    }
}
```
