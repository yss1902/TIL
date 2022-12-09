## 1. 학급 회장
```
	public char solution(int n, String s) {
		char answer = ' ';
		HashMap<Character, Integer> map = new HashMap<>();
		for (char key : s.toCharArray()) {
			map.put(key, map.getOrDefault(key, 0) + 1); //중요. get은 x의 키 값을 가져옴.
		} // 없더라면 0을 리턴함.

		int max = Integer.MIN_VALUE;
		for (char key : map.keySet()) { //최대 밸류값의 키를 알아내기. 존재하는 키들을 탐색 set
			if (map.get(key) > max) { //키의 값을 가져옴 get
				max = map.get(key);
				answer = key;
			}
		}
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		int n = kb.nextInt();
		String str = kb.next();
		System.out.println(T.solution(n, str));
	}
}
```
## 2. 아나그램
```
class Main {	
	public String solution(String s1, String s2){
		String answer="YES";
		HashMap<Character, Integer> map=new HashMap<>();
		for(char x : s1.toCharArray()){
			map.put(x, map.getOrDefault(x, 0)+1);
		}
		for(char x : s2.toCharArray()){
			if(!map.containsKey(x) || map.get(x)==0) return "NO";
			map.put(x, map.get(x)-1); //아래가아니라면 아나그램이맞으므로 이줄을실행
		} //x라는키가존재안하고 or 키가존재한다면 -1감소시켜야하는데 개수가일치하지않음
		return answer;
	}

	public static void main(String[] args){
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		String a=kb.next();
		String b=kb.next();
		System.out.print(T.solution(a, b));
	}
}
```
## 3. 매출액의 종류(Hash, sliding window)
```
	public ArrayList<Integer> solution(int n, int k, int[] arr) {
		ArrayList<Integer> answer = new ArrayList<>();
		HashMap<Integer, Integer> HM = new HashMap<>();
		for (int i = 0; i < k - 1; i++) { //하루적게해서세팅
			HM.put(arr[i], HM.getOrDefault(arr[i], 0) + 1);
		}
		int lt = 0;
		for (int rt = k - 1; rt < n; rt++) {
			HM.put(arr[rt], HM.getOrDefault(arr[rt], 0) + 1);
			answer.add(HM.size());
			HM.put(arr[lt], HM.get(arr[lt]) - 1);
			if (HM.get(arr[lt]) == 0)
				HM.remove(arr[lt]);
			lt++;
		}
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		int n = kb.nextInt();
		int k = kb.nextInt();
		int[] arr = new int[n];
		for (int i = 0; i < n; i++) {
			arr[i] = kb.nextInt();
		}
		for (int x : T.solution(n, k, arr))
			System.out.print(x + " ");
	}
}
```
## 4. 모든 아나그램 찾기(Hash, sliding window : 시간복잡도 O(n))
```
	public int solution(String a, String b) {
		int answer = 0;
		HashMap<Character, Integer> am = new HashMap<>();
		HashMap<Character, Integer> bm = new HashMap<>();
		for (char x : b.toCharArray())
			bm.put(x, bm.getOrDefault(x, 0) + 1);
		int L = b.length() - 1;
		for (int i = 0; i < L; i++)
			am.put(a.charAt(i), am.getOrDefault(a.charAt(i), 0) + 1);
		int lt = 0;
		for (int rt = L; rt < a.length(); rt++) {
			am.put(a.charAt(rt), am.getOrDefault(a.charAt(rt), 0) + 1);
			if (am.equals(bm))
				answer++;
			am.put(a.charAt(lt), am.get(a.charAt(lt)) - 1);
			if (am.get(a.charAt(lt)) == 0)
				am.remove(a.charAt(lt));
			lt++;
		}
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		String a = kb.next();
		String b = kb.next();
		System.out.print(T.solution(a, b));
	}
}
```
## 5. K번째 큰 수
```
	public int solution(int[] arr, int n, int k) {
		int answer = -1;
		TreeSet<Integer> Tset = new TreeSet<>(Collections.reverseOrder());
		for (int i = 0; i < n; i++) {
			for (int j = i + 1; j < n; j++) {
				for (int l = j + 1; l < n; l++) {
					Tset.add(arr[i] + arr[j] + arr[l]);
				}
			}
		}
		int cnt = 0;

		for (int x : Tset) {
			cnt++;
			if (cnt == k)
				return x;
		}
		return answer;
	}

	public static void main(String[] args) {
		Main T = new Main();
		Scanner kb = new Scanner(System.in);
		int n = kb.nextInt();
		int k = kb.nextInt();
		int[] arr = new int[n];
		for (int i = 0; i < n; i++) {
			arr[i] = kb.nextInt();
		}
		System.out.println(T.solution(arr, n, k));
	}
}
```
