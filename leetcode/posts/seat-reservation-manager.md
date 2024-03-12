---
title: Seat Reservation Manager
summary: Seat Reservation Manager - Solution Explained
url: "/posts/seat-reservation-manager"
date: 2020-09-09T03:00:00
tags: ["leetcode", "problem-solving"]
series: [leetcode]
keywords: ["Seat Reservation Manager LeetCode Solution Explained in all languages", "1845", "leetcode question 1845", "Seat Reservation Manager", "LeetCode", "leetcode solution in Python3 C++ Java Go PHP Ruby Swift TypeScript Rust C# JavaScript C", "GeeksforGeeks", "InterviewBit", "Coding Ninjas", "HackerRank", "HackerEarth", "CodeChef", "TopCoder", "AlgoExpert", "freeCodeCamp", "Codeforces", "GitHub", "AtCoder", "Samir Paul"]
cover:
    image: https://spcdn.pages.dev/leetcode/images/seat-reservation-manager.webp
    alt: Seat Reservation Manager - Solution Explained
    hiddenInList: true
    hiddenInSingle: false
math: true
---


# [1845. Seat Reservation Manager](https://leetcode.com/problems/seat-reservation-manager)


## Description

<p>Design a system that manages the reservation state of <code>n</code> seats that are numbered from <code>1</code> to <code>n</code>.</p>

<p>Implement the <code>SeatManager</code> class:</p>

<ul>
	<li><code>SeatManager(int n)</code> Initializes a <code>SeatManager</code> object that will manage <code>n</code> seats numbered from <code>1</code> to <code>n</code>. All seats are initially available.</li>
	<li><code>int reserve()</code> Fetches the <strong>smallest-numbered</strong> unreserved seat, reserves it, and returns its number.</li>
	<li><code>void unreserve(int seatNumber)</code> Unreserves the seat with the given <code>seatNumber</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<pre>
<strong>Input</strong>
[&quot;SeatManager&quot;, &quot;reserve&quot;, &quot;reserve&quot;, &quot;unreserve&quot;, &quot;reserve&quot;, &quot;reserve&quot;, &quot;reserve&quot;, &quot;reserve&quot;, &quot;unreserve&quot;]
[[5], [], [], [2], [], [], [], [], [5]]
<strong>Output</strong>
[null, 1, 2, null, 2, 3, 4, 5, null]

<strong>Explanation</strong>
SeatManager seatManager = new SeatManager(5); // Initializes a SeatManager with 5 seats.
seatManager.reserve();    // All seats are available, so return the lowest numbered seat, which is 1.
seatManager.reserve();    // The available seats are [2,3,4,5], so return the lowest of them, which is 2.
seatManager.unreserve(2); // Unreserve seat 2, so now the available seats are [2,3,4,5].
seatManager.reserve();    // The available seats are [2,3,4,5], so return the lowest of them, which is 2.
seatManager.reserve();    // The available seats are [3,4,5], so return the lowest of them, which is 3.
seatManager.reserve();    // The available seats are [4,5], so return the lowest of them, which is 4.
seatManager.reserve();    // The only available seat is seat 5, so return 5.
seatManager.unreserve(5); // Unreserve seat 5, so now the available seats are [5].
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>1 &lt;= seatNumber &lt;= n</code></li>
	<li>For each call to <code>reserve</code>, it is guaranteed that there will be at least one unreserved seat.</li>
	<li>For each call to <code>unreserve</code>, it is guaranteed that <code>seatNumber</code> will be reserved.</li>
	<li>At most <code>10<sup>5</sup></code> calls <strong>in total</strong> will be made to <code>reserve</code> and <code>unreserve</code>.</li>
</ul>

## Solutions

### Solution 1: Priority Queue (Min Heap)

We can use a priority queue (min heap) to maintain the smallest number of reservable seats.

Initially, put all seat numbers into the priority queue.

When the `reserve` method is called, take out the smallest number from the priority queue, which is the smallest number of reservable seats.

When the `unreserve` method is called, put the seat number back into the priority queue.

The time complexity is $O(n \times \log n)$, and the space complexity is $O(n)$. Where $n$ is the number of seats.

<!-- tabs:start -->

{{< terminal title="Python Code" >}}
```python
class SeatManager:
    def __init__(self, n: int):
        self.q = list(range(1, n + 1))
        heapify(self.q)

    def reserve(self) -> int:
        return heappop(self.q)

    def unreserve(self, seatNumber: int) -> None:
        heappush(self.q, seatNumber)


# Your SeatManager object will be instantiated and called as such:
# obj = SeatManager(n)
# param_1 = obj.reserve()
# obj.unreserve(seatNumber)
```
{{< /terminal >}}

{{< terminal title="Java Code" >}}
```java
class SeatManager {
    private PriorityQueue<Integer> q = new PriorityQueue<>();

    public SeatManager(int n) {
        for (int i = 1; i <= n; ++i) {
            q.offer(i);
        }
    }

    public int reserve() {
        return q.poll();
    }

    public void unreserve(int seatNumber) {
        q.offer(seatNumber);
    }
}

/**
 * Your SeatManager object will be instantiated and called as such:
 * SeatManager obj = new SeatManager(n);
 * int param_1 = obj.reserve();
 * obj.unreserve(seatNumber);
 */
```
{{< /terminal >}}

{{< terminal title="C++ Code" >}}
```cpp
class SeatManager {
public:
    SeatManager(int n) {
        for (int i = 1; i <= n; ++i) {
            q.push(i);
        }
    }

    int reserve() {
        int seat = q.top();
        q.pop();
        return seat;
    }

    void unreserve(int seatNumber) {
        q.push(seatNumber);
    }

private:
    priority_queue<int, vector<int>, greater<int>> q;
};

/**
 * Your SeatManager object will be instantiated and called as such:
 * SeatManager* obj = new SeatManager(n);
 * int param_1 = obj->reserve();
 * obj->unreserve(seatNumber);
 */
```
{{< /terminal >}}

{{< terminal title="Go Code" >}}
```go
type SeatManager struct {
	q hp
}

func Constructor(n int) SeatManager {
	q := hp{}
	for i := 1; i <= n; i++ {
		heap.Push(&q, i)
	}
	return SeatManager{q}
}

func (this *SeatManager) Reserve() int {
	return heap.Pop(&this.q).(int)
}

func (this *SeatManager) Unreserve(seatNumber int) {
	heap.Push(&this.q, seatNumber)
}

type hp struct{ sort.IntSlice }

func (h hp) Less(i, j int) bool { return h.IntSlice[i] < h.IntSlice[j] }
func (h *hp) Push(v any)        { h.IntSlice = append(h.IntSlice, v.(int)) }
func (h *hp) Pop() any {
	a := h.IntSlice
	v := a[len(a)-1]
	h.IntSlice = a[:len(a)-1]
	return v
}

/**
 * Your SeatManager object will be instantiated and called as such:
 * obj := Constructor(n);
 * param_1 := obj.Reserve();
 * obj.Unreserve(seatNumber);
 */
```
{{< /terminal >}}

{{< terminal title="C# Code" >}}
```cs
public class SeatManager {
    private SortedSet<int> availableSeats;

    public SeatManager(int n) {
        availableSeats = new SortedSet<int>();
        for (int i = 1; i <= n; i++) {
            availableSeats.Add(i);
        }
    }

    public int Reserve() {
        int reservedSeat = availableSeats.Min;
        availableSeats.Remove(reservedSeat);
        return reservedSeat;
    }

    public void Unreserve(int seatNumber) {
        availableSeats.Add(seatNumber);
    }
}

/**
 * Your SeatManager object will be instantiated and called as such:
 * SeatManager obj = new SeatManager(n);
 * int param_1 = obj.Reserve();
 * obj.Unreserve(seatNumber);
 */
```
{{< /terminal >}}

<!-- tabs:end -->

<!-- end -->
