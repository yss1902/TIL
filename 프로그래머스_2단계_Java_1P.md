올바른 괄호
```
import java.util.*;

class Solution {
	boolean solution(String s) {
		boolean answer = true;

		Stack<Character> stack = new Stack<>();

		for (int i = 0; i < s.length(); i++) {
			if (s.charAt(i) == '(')
				stack.push('(');
			else {
				if (stack.isEmpty())
					return false;
				else
					stack.pop();
			}
		}
		answer = (stack.isEmpty()) ? true : false;

		return answer;
	}
}
```
최솟값 만들기
```
import java.util.*;

class Solution {
	public int solution(int[] A, int[] B) {
		int answer = 0;

		Arrays.sort(A);
		Arrays.sort(B);

		for (int i = 0; i < A.length; i++) {
			answer += A[i] * B[B.length - 1 - i];
		}

		return answer;
	}
}
```
JadenCase 문자열 만들기
```
class Solution {
  public String solution(String s) {
        String answer = "";
        String[] sp = s.toLowerCase().split("");
        boolean flag = true;

        for(String ss : sp) {
            answer += flag ? ss.toUpperCase() : ss;
            flag = ss.equals(" ") ? true : false;
        }

        return answer;
  }
}
```
```
import java.util.*;

class Solution {
    public String solution(String s) {
        String answer = "";
    	
    	// " " 기준으로 문자열 잘라서 배열에 넣음
    	String[] arr = s.split(" ");
    	// 잘린 문자열을 순서대로 처리
    	for(int i=0; i<arr.length; i++) {
    		String now = arr[i];
    		
    		// 문자열의 길이가 0이라면(공백 이라면)
    		// answer에 " "만 추가
    		if(arr[i].length() == 0) {
    			answer += " ";
    		} 
    		// 문자가 있다면
    		else {
    			// 0번째 문자는 대문자로
    			answer += now.substring(0, 1).toUpperCase();
    			// 1번째 문자부터 마지막까지는 소문자로
    			answer += now.substring(1, now.length()).toLowerCase();
    			// 마지막에 " " 추가
    			answer += " ";
    		}
    		
    	}
    	
    	// 입력 받은 문자열의 맨 마지막이 " " 라면 바로 answer 반환
    	if(s.substring(s.length()-1, s.length()).equals(" ")){
    		return answer;
    	}
    	
    	// 맨 마지막 " " 제거하고 answer 반환
        return answer.substring(0, answer.length()-1);
    }

}
```
최댓값과 최솟값
```
class Solution {
	public String solution(String s) {
		String answer = "";

		String[] number = s.split(" ");
		int min = Integer.MAX_VALUE;
		int max = Integer.MIN_VALUE;

		for (int i = 0; i < number.length; i++) {
			int num = Integer.parseInt(number[i]);

			min = Math.min(min, num);
			max = Math.max(max, num);
			answer = min + " " + max;
		}

		return answer;
	}
}
```
이진 변환 반복하기
```
class Solution {
	public int[] solution(String s) {
		int[] answer = new int[2];

		while (s.length() > 1) {

			int cnt1 = 0;
			for (int i = 0; i < s.length(); i++) {

				if (s.charAt(i) == '0')
					answer[1]++;
				else
					cnt1++;
			}

			s = Integer.toBinaryString(cnt1);
			answer[0]++;
		}

		return answer;
	}
}
```
숫자의표현
```
import java.util.*;

class Solution {
	public int solution(int n) {
		int answer = 0;

		for (int i = 1; i <= n; i++) {
			int sum = 0;
			for (int j = i; j <= n; j++) {
				sum += j;

				if (sum == n) {
					answer++;
					break;
				} else if (sum > n) {
					break;
				}
			}
		}
		return answer;
	}
}
```
피보나치 수
```
import java.util.*;

class Solution {
	public int solution(int n) {
		int answer[] = new int[n + 1];
		for (int i = 0; i <= n; i++) {
			if (i == 0)
				answer[i] = 0;
			else if (i == 1)
				answer[i] = 1;
			else {
				int sum = answer[i - 2] + answer[i - 1];
				answer[i] = sum % 1234567;
			}
		}

		return answer[n];
	}
}
```
다음 큰 숫자
```
import java.util.*;

class Solution {
	public int solution(int n) {
		int answer = 0;
		int n_cnt = Integer.bitCount(n); // 입력받은 n의 1 개수를 저장.
		int b_cnt = 0; // 증가하는 n의 1 개수를 저장 할 변수.
		while (true) {
			n++; // n을 증가.
			b_cnt = Integer.bitCount(n); // 증가된 n의 1 개수를 저장.
			if (n_cnt == b_cnt) { // 일치하면, answer에 n을 담고 반복문을 빠져나온다.
				answer = n;
				break;
			}
		} //bitCount: 입력된 정수를 2진수로 변환한 뒤, 2진수에 포함된 1을 카운팅 해주는 메소드

		return answer;
	}
}
```
카펫
```
import java.util.*;

class Solution {
	public int[] solution(int brown, int yellow) {
		int[] answer = new int[2];

		int area = brown + yellow; // 전체 갯수
		// area의 약수를 구해야 한다. (카펫 사이즈의 경우의 수)

		// 행과 열의 갯수는 3이상이여야 합니다.
		for (int i = 3; i <= area; i++) {
			int col = i; // 열
			int row = area / col; // 행

			// 행의 갯수가 3이하이면 Pass합니다.
			if (row < 3) {
				continue;
			}

			// 행은 열보다 크거나 같아야 합니다.
			if (row >= col) {
				// 문제의 규칙에 의하면 row-2*col-2 = yellow 입니다.
				if ((row - 2) * (col - 2) == yellow) {
					answer[0] = row;
					answer[1] = col;
					return answer;
				}
			}

		}
		return answer;
	}
}
```
짝지어 제거하기
```
import java.util.*;

class Solution {
	public int solution(String s) {
		int answer = -1;
		char[] carr = s.toCharArray();
		Stack<Character> stack = new Stack<>();
		//문제에서 짝 이라는 단어는 stack을 의미하는 경우가 많은 것 같습니다.

		for (int i = 0; i < carr.length; i++) {
			char c = carr[i];
			// 스택이 비어있다면 현재 문자는 반복될 일이 없으므로 push
			if (stack.isEmpty())
				stack.push(c);
			// 스택이 비어있지 않다면
			else {
				// 스택의 top확인(peek) - 만약 현재 문자와 같다면 반복이므로 스택에서 pop하고 현재 문자도 스택에 넣지 않음
				// 이렇게 되면 스택에는 반복이 발생하는 이전문자와 현재문자 모두 들어가지 않게 됨 (반복제거)
				if (stack.peek() == c) {
					stack.pop();
					// 스택의 top이 현재 문자와 다르다면 반복이 아니므로 push
				} else {
					stack.push(c);
				}
			}
		}
		// 스택에 남아있는 값들은 반복되지 않는 값들임 즉, 비어있어다면 모두 짝지어 반복된 것
		return stack.isEmpty() ? 1 : 0;
	}
}
```
영어 끝말잇기
```
import java.util.*;

class Solution {
	public int[] solution(int n, String[] words) {
		int[] answer = new int[2];
		List<String> list = new ArrayList<String>();
		boolean flag = true;

		for (int i = 0; i < words.length; i++) {
			if (list.contains(words[i])) { // 이전에 등장한 단어인경우
				answer[0] = (i % n) + 1; 
				answer[1] = (i / n) + 1;
				flag = false;
				break;
			} /*0, 3, 6 을 3으로 나눴을경우 나머지는 모두 0이다. 따라서 여기에 +1을 해주면 첫번째 사람이 된다.
			  따라서 규칙은 answer[0] = i%n + 1 이 된다.
			  0, 1, 2를 3으로 나눴을경우 몫은 0이다. 따라서 여기에 +1을 해주면 첫번째 차례가 된다.
			  따라서 규칙은 answer[1] = i/n + 1 이 된다.
			  */

			list.add(words[i]); // 현재 단어 리스트에 넣기

			// 이전 끝단어와 현재 첫단어가 다른경우 - 끝말잇기가 아닌경우
			if (i > 0 && words[i - 1].charAt(words[i - 1].length() - 1) != words[i].charAt(0)) {
				answer[0] = (i % n) + 1;
				answer[1] = (i / n) + 1;
				flag = false;
				break;
			}
		}
		if (flag)
			return new int[] { 0, 0 };
		return answer;
	}
}
```
