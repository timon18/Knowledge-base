28-03-2023
11:07
Authors: Tamerlan Khutuev
***
Tags: #patterns 
***
# Адаптер
Также известен как: Wrapper, Обёртка, Adapter
https://refactoring.guru/ru/design-patterns/adapter

Паттерн адаптер (Adapter) используется для преобразования интерфейса одного класса в интерфейс другого класса, который ожидают клиенты. Это позволяет объектам с несовместимыми интерфейсами работать вместе.

## Проблема.
У нас есть готовый интерфейс (A) который мы не должны менять. А так же готовый класс (B) который не имплементирует этот интерфейс. Но надо сделать так, что бы метод который принимает интерфейс (A) мог принять класс (B). 
Либо у нас есть данные которые приходят в одном формате и библиотека которая принимает данные в другом формате. 

## Решение
Можно создать объект-переводчик (прослойку) которая будет трансформировать интерфейс либо данные объекта в другой вид который подходит для другого объекта. 

## Пример
```java
// Целевой интерфейс, который ожидают клиенты
interface MediaPlayer {
   public void play(String audioType, String fileName);
}

// Адаптируемый класс
class AudioPlayer {
   public void playMp3(String fileName) {
      System.out.println("Playing mp3 file. Name: " + fileName);
   }
}

// Адаптер класс, который преобразует интерфейс AudioPlayer в MediaPlayer
class MediaAdapter implements MediaPlayer {

   AudioPlayer audioPlayer = new AudioPlayer();

   public void play(String audioType, String fileName) {

      if(audioType.equalsIgnoreCase("mp3")) {
         audioPlayer.playMp3(fileName);
      }
   }
}

// Клиентский код который ожидает имплементацию MediaPlayer
class AudioPlayerClient {
   public void playAudio(MediaPlayer mediaPlayer) {
      mediaPlayer.play("mp3", "song.mp3");
   }
}
```