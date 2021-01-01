---
title: 'Array'
date: 2021-01-01 00:00:00
category: 'Algorithms'
draft: false
---
## Array

메모리 상에 원소를 연속하게 배치한 자료구조

### 성질

1. O(1)에 k번째 원소를 확인 / 변경 가능
2. 추가적으로 소모되는 메모리의 양(=overhead)가 거의 없음
3. Cache hit rate가 높음
4. 메모리 상에 연속한 구간을 잡아야해서 할당에 제약이 걸림

### 시간복잡도

- 임의의 위치에 있는 원소를 확인/ 변경 : O(1)
- 원소 끝에 추가 : O(1)
- 임의의 위치에 원소를 추가, 제거 : O(N)

### ✍️예제문제

배열 insert, erase 함수 구현하기

> insert

```cpp
void insert(int index, int num, int arr[], int& len) {
	for(int i = len; i > index ; i--) arr[i] = arr[i - 1];
	arr[index] = num;
	len++;
}
```

> erase

```cpp
void erase(int index, int arr[], int& len) {
	len--;
	for(int i = idx; i < len; i++) arr[i] = arr[i + 1] ;
}
```

전체를 특정 값으로 초기화시킬 때 어떻게 하면 효율적으로 할 수 있을까? 🤔

⭐⭐ **fill 함수 사용**

```cpp
// fill(array, array+sizeOfArray, number);
int a[21];
fill(a, a+21; 0);
```

---

### ✍️예제문제

> 알파벳 소문자로만 이루어진 단어 S가 주어진다. 각 알파벳이 단어에 몇 개가 포함되어 있는지 구하는 프로그램을 작성하시오.

```cpp
int count[26] = {};
    string str;
    cin >> str;
    for(int i=0;i<str.size();i++) {
        count[str[i] - 'a']++;
    }
    for(int i = 0;i<26;i++) {
        cout << count[i] << " ";
    }
```

> 주어진 길이 N의 int 배열 arr에서 합이 100인 서로 다른 위치의 두 원소가 존재하면 1을, 존재하지 않으면 0을 반환하는 함수 func2(int arr[], int N)을 작성하라. arr의 각 수는 0 이상 100 이하이고 N은 1000 이하이다.

```cpp
int func2(int arr[], int N) {
    int count[101];
    for(int i=0;i<N;i++) {
        count[arr[i]] = 1;
        // if(count[100 - i])
        if(count[100 - i] == 1) return 1;
    }
    return 0;
}
```