# 🟡 Top K Frequent Elements - Medium

![Top K Frequent Elements](/img/Top%20K%20Frequent%20Elements.png)

```JS
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number[]}
 */
var topKFrequent = function(nums, k) {
    const count = {}
    const freq = Array.from({ length: nums.length + 1 }, () => [])

    for (const n of nums) {
        count[n] = (count[n] || 0) + 1
    }

    for (const n in count) {
        freq[count[n]].push(parseInt(n))
    }

    const res = []
    for (let i = freq.length - 1; i > 0; i--) {
        for (const n of freq[i]) {
            res.push(n)
            if (res.length === k) {
                return res
            }
        }
    }
};
```
