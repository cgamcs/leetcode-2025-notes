# Contains Duplicate

![Contains Duplicate](/img/Contains%20Duplicate.png)

```JS
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
    const seen = new Set()

    for (const num of nums) {
        if (seen.has(num)) {
            return true
        }

        seen.add(num)
    }
    return false
};
```