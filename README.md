# Scanner를 이용한 숫자야구게임
Java
## 설명

```java
Random random = new Random();
Scanner scanner = new Scanner(System.in);
  ```
scanner와 randeom를 만든다.<br>

```java
//게임에서 사용할 변수
int com1, com2, com3;		
int user1, user2, user3;
int randomCnt = 0;//난수생성 카운트
int gameCount = 0;//게임 카운트
int strikeCnt = 0;//스트라이크 카운트
int ballCnt = 0;//볼 카운트
```
숫자와 사용자, 난수생성, 게임 카운트, 스트라이크 카운트, 볼 카운트를 선언해준다.<br>

```java
//게임전체반복	
while(true) {		
	//중복되지 않는 3개의 난수생성
	while(true) {
		//몇번만에 난수가 생성되는지 확인
		randomCnt++;				
	  //1~9사이의 난수생성
		com1 = random.nextInt(100) % 9 + 1;
		com2 = random.nextInt(100) % 9 + 1;
		com3 = random.nextInt(100) % 9 + 1;
		if(!(com1==com2 || com2==com3 || com3==com1)) {				
			//중복되지 않는 난수 생성에 성공하면 루프탈출
			break;
		}
	}////while end
```
반복문 생성 후 중복되지 않는 3개의 난수를 생성해서 성공하면 반복문에서 브레이크를 걸어 탈출시킨다.<br>

```java
//난수확인
//System.out.println(randomCnt+"회:"+com1+" "+com2+" "+com3);
```
난수확인을 할 사람은 만들어도 좋다. 하지만 안 하는게 더 좋다.<br>

```java
while(true) {
				//사용자로부터 3개의 정수를 입력받는다.
				System.out.println("3개의정수를 입력하세요(1~9)");
				System.out.println("스페이스로 구분하시고 마지막에 Enter를 눌러주세요");				
				user1 = scanner.nextInt();
				user2 = scanner.nextInt();
				user3 = scanner.nextInt();
					
				//게임카운트 1회 증가
				gameCount++;
					
				//판단1 - 스트라이크(숫자와 위치까지 일치)
				if(com1==user1) strikeCnt++;
				if(com2==user2) strikeCnt++;
				if(com3==user3) strikeCnt++;
					
				//판단2 - 볼(숫자는 일치하나 위치가 다를때)
				if(com1==user2 || com1==user3) ballCnt++;
				if(com2==user1 || com2==user3) ballCnt++;
				if(com3==user1 || com3==user2) ballCnt++;
					
			//게임종료판단
			if(strikeCnt==3) {
				System.out.println("3스트라이크 게임종료");
				System.out.println(gameCount+"번만에 맞추셨습니다.");
				break;//루프탈출
			}
			else {
				//하나도 못맞추는 경우
				if(strikeCnt==0 && ballCnt==0) {
					System.out.println("아웃입니다");
				}
				else {
					System.out.printf("%d스트라이크, %d볼\n", strikeCnt, ballCnt);
					}
					//스트라이크, 볼 카운트 초기화
					strikeCnt = 0;
					ballCnt = 0;
					//continue문은 필요없음.
				}
			}////while end
   ```
사용자로부터 3개의 정수를 입력받고 게임카운트 1회 증가시킨 다음 볼과 스트라이크를 판단시키고 게임을 종료시킨다.<br>

```java
System.out.println("한게임 더 하시겠습니까?(0:종료,1:재시작)");
			int restart = scanner.nextInt();
			if(restart==0) {
				//게임종료
				System.out.println("\n==게임이 종료되었습니다.==\n");
				//실행되는 즉시 main함수가 종료된다.
				System.exit(0);
			}
			else if(restart==1){
				//게임을 재시작하기 위해 카운트변수 초기화
				strikeCnt = 0;
				ballCnt = 0;
				gameCount = 0;
				System.out.println("\n==게임을 재시작합니다.==\n");
				}
			}//게임 전체 반복 while end
  ```
각 상황에 맞는 메세지를 띄운다. int restart를 선언해 0을 넣을시 게임이 종료되고 1을 넣으면 재시작이 되도록 만든다.<br>
카운트변수들도 초기화 시킨다.<br>

## 풀코드
```java
package sungil0616;

import java.util.*;

public class Baseball2 {
		
	public static void main(String[] args) {
		
		Random random = new Random();
		Scanner scanner = new Scanner(System.in);
			
		//게임에서 사용할 변수
		int com1, com2, com3;		
		int user1, user2, user3;
		int randomCnt = 0;//난수생성 카운트
		int gameCount = 0;//게임 카운트
		int strikeCnt = 0;//스트라이크 카운트
		int ballCnt = 0;//볼 카운트
			
		//게임전체반복	
		while(true) {		
			//중복되지 않는 3개의 난수생성
			while(트라이크(숫자와 위치까지 일치)
				if(com1==user1) strikeCnt++;
				if(com2==user2) strikeCnt++;
				if(com3==user3) strikeCnt++;
					
				//판단2 - 볼(숫자는 일치하나 위치가 다를때)
				if(com1==user2 || com1==user3) ballCnt++;
				if(com2==user1 || com2==user3) ballCnt++;
				if(com3==user1 || com3==user2) ballCnt++;
					
			//게임종료판단
			if(strikeCnt==3) {
				System.out.println("3스트라이크 게임종료");
				System.out.println(gameCount+"번만에 맞추셨습니다.");
				break;//루프탈출
			}
			else {
				//하나도 못맞추는 경우
				if(strikeCnt==0 && ballCnt==0) {
					System.out.println("아웃입니다");
				}
				else {
					System.out.printf("%d스트라이크, %d볼\n", strikeCnt, ballCnt);
					}
					//스트라이크, 볼 카운트 초기화
					strikeCnt = 0;
					ballCnt = 0;
					//continue문은 필요없음.
				}
			}////while end
				
			System.out.println("한게임 더 하시겠습니까?(0:종료,1:재시작)");
			int restart = scanner.nextInt();
			if(restart==0) {
				//게임종료
				System.out.println("\n==게임이 종료되었습니다.==\n");
				//실행되는 즉시 main함수가 종료된다.
				System.exit(0);
			}
			else if(restart==1){
				//게임을 재시작하기 위해 카운트변수 초기화
				strikeCnt = 0;
				ballCnt = 0;
				gameCount = 0;
				System.out.println("\n==게임을 재시작합니다.==\n");
				}
			}//게임 전체 반복 while end
	}//main 메서드 end
}//class 끝
```

## 실행결과
### 0을 넣은 결과
![image](https://github.com/Poki742/BaseBallGame/assets/126844692/e41ad765-72d0-4f8b-bc9e-1d3fc39889b7)<br>

### 1을 넣은 결과
![image](https://github.com/Poki742/BaseBallGame/assets/126844692/f74e5440-d77f-4f17-b4ca-d66eb782513e)<br>

