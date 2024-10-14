---
title: "[Java] Collection과 Map"
date: 2024-05-03 19:10:00 +0900
categories:
  - docs
  - java
tags:
  - java
  - ArrayList
  - List
  - Set
  - HashMap
  - TreeMap
layout: single
---
# Java Collection과 Map

## 1. Java Collection

- Java Collection은 데이터를 저장하고 조작할 수 있는 구조를 제공하며, `java.util` 패키지에 포함된 인터페이스와 클래스의 집합이다. 데이터를 순서대로 저장하거나 중복을 허용하지 않는 방식 등 다양한 요구사항에 맞춰 사용할 수 있다.

### 주요 Collection 인터페이스
1. **List 인터페이스**  
   - **List**는 순서가 있는 데이터의 집합을 다루며, 중복 요소를 허용한다. 대표적으로 `ArrayList`와 `LinkedList`가 있다.
   - **ArrayList 예제**:
     ```java
     import java.util.ArrayList;
     
     public class ListExample {
         public static void main(String[] args) {
             ArrayList<String> fruits = new ArrayList<>();
             fruits.add("Apple");
             fruits.add("Banana");
             fruits.add("Orange");
             fruits.add("Apple"); // 중복 허용

             for (String fruit : fruits) {
                 System.out.println(fruit);
             }
         }
     }
     ```
     위 코드는 `ArrayList`를 사용해 "Apple", "Banana", "Orange", "Apple"을 저장하고 출력한다.

2. **Set 인터페이스**  
   - **Set**은 순서가 없는 데이터의 집합을 다루며, 중복 요소를 허용하지 않는다. `HashSet`과 `TreeSet`이 주로 사용된다.
   - **HashSet 예제**:
     ```java
     import java.util.HashSet;
     
     public class SetExample {
         public static void main(String[] args) {
             HashSet<String> fruits = new HashSet<>();
             fruits.add("Apple");
             fruits.add("Banana");
             fruits.add("Orange");
             fruits.add("Apple"); // 중복 요소는 무시된다.

             for (String fruit : fruits) {
                 System.out.println(fruit);
             }
         }
     }
     ```
     위 코드는 "Apple"을 두 번 추가해도 중복이 허용되지 않기 때문에 한 번만 저장된다.

3. **Queue 인터페이스**  
   - **Queue**는 선입선출(FIFO) 방식으로 요소를 처리한다. `LinkedList`나 `PriorityQueue`가 사용된다.
   - **Queue 예제**:
     ```java
     import java.util.LinkedList;
     import java.util.Queue;

     public class QueueExample {
         public static void main(String[] args) {
             Queue<String> queue = new LinkedList<>();
             queue.add("First");
             queue.add("Second");
             queue.add("Third");

             System.out.println("Queue head: " + queue.peek()); // 첫 번째 요소 확인
             System.out.println("Removed: " + queue.poll()); // 첫 번째 요소 제거
             System.out.println("Queue head after removal: " + queue.peek());
         }
     }
     ```
     `poll()` 메서드는 큐에서 첫 번째 요소를 제거하고 반환한다.

## 2. Java Map

- **Map**은 키와 값의 쌍으로 데이터를 저장하며, 중복된 키를 허용하지 않는다. 대표적으로 `HashMap`, `TreeMap`, `LinkedHashMap`이 있다.

1. **HashMap 예제**
   - **HashMap**은 순서를 보장하지 않으며, 키와 값으로 데이터를 관리한다.
   ```java
   import java.util.HashMap;

   public class MapExample {
       public static void main(String[] args) {
           HashMap<String, Integer> map = new HashMap<>();
           map.put("Apple", 1);
           map.put("Banana", 2);
           map.put("Orange", 3);
           map.put("Apple", 4); // 기존 키 "Apple"의 값을 덮어쓴다.

           for (String key : map.keySet()) {
               System.out.println("Key: " + key + ", Value: " + map.get(key));
           }
       }
   }

2. **TreeMap 예제**
  - TreeMap은 키의 자연 순서(혹은 제공된 Comparator)에 따라 정렬된다.
  ```java
  import java.util.TreeMap;

  public class TreeMapExample {
      public static void main(String[] args) {
          TreeMap<String, Integer> map = new TreeMap<>();
          map.put("Banana", 2);
          map.put("Apple", 1);
          map.put("Orange", 3);

          for (String key : map.keySet()) {
              System.out.println("Key: " + key + ", Value: " + map.get(key));
          }
      }
  }
  ```
  이 코드는 키가 알파벳 순서로 정렬되어 출력된다.

이처럼 Java의 Collection과 Map은 다양한 데이터 저장 및 관리 방식을 제공하여 개발자가 상황에 맞는 자료 구조를 선택해 사용할 수 있게 해준다.