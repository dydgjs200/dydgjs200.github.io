---
layout : post
title : "PriorityQueue(우선순위 큐) 와 예제"
---



큐에 관한 문제를 풀다 알게 된 PriorityQueue에 대해 포스팅하려한다.

단순하게 정렬해주는 큐 라고 생각하면 될 것 같다.

예제를 통해 알아보자면



~~~java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        PriorityQueue<Integer> que = new PriorityQueue<>();

        for(int i=0; i<5; i++){
            que.add(scanner.nextInt());
        }

        for(int i:que){
            System.out.println(i);
        }
    }
}
~~~

이런식으로 que를 선언한 뒤 입력을 아래와 같이 넣는다면

~~~
123	
489
15
7
999
-----입력
7
15
123
489
999
-----출력
~~~

정렬이 되어서 나오는 것을 알 수 있다!(물론 메모리를 많이 쓰는 단점이 있다..)

문자열도 정렬이 되어서 나온다.

~~~
ab
af
ad
ac
ke
---------
ab
ac
ad
af
ke
~~~



또한 내림차순으로 정렬하기 위해서는 큐를 선언할 때 아래와 같이 선언하면 된다(comparator를 사용하면 된다.)

~~~java
PriorityQueue<String> que = new PriorityQueue<>(Comparator.reverseOrder());
~~~



이에 대한 예제는 _백준 1927 최소힙_  문제가 있다.

배열에 자연수를 넣고 앞에서 부터 빼내야하기 때문에 Queue를 사용하고, 작은수를 정렬해야하므로 PriorityQueue 를 이용해야한다.

~~~java
import java.util.*;

public class Main {
    static int n;
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        n = scanner.nextInt();
            Queue<Integer> que = new LinkedList<>();
        PriorityQueue<Integer> prioque = new PriorityQueue<>();

        for(int i=0; i<n; i++){
            int num = scanner.nextInt();
            que.add(num);

            if(que.poll() == 0){
                if(prioque.isEmpty())
                    System.out.println(0);
                else{
                    System.out.println(prioque.poll());
                }
            }
            else{
                prioque.add(num);
            }
        }
    }
}
~~~

또한 문제에서 큐에 0이 아닌 자연수가 없으면 0을 출력하라 했으므로 맨 앞에 있는 원소가 0인지만 체크해준 뒤 자연수를 넣는 que인 prioque가 비어있다면 0을 출력, 아니라면 자연수를 빼내주면 된다.

