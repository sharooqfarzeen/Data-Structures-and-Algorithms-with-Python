from typing import List


class Solution:

    def calculate_hash_str(self, freq: List[int]) -> str:
        str_freq = [str(num) for num in freq]
        return "$".join(str_freq)

    def calculate_freq_arr(self, word: str) -> List[int]:
        freq = [0 for _ in range(26)]
        for i in range(len(word)):
            freq[ord(word[i]) - ord('a')] += 1
        return freq

    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        ans = []
        hashtable = dict()

        for word in strs:
            freq_arr = self.calculate_freq_arr(word)
            hash_str = self.calculate_hash_str(freq_arr)
            if hashtable.get(hash_str, None):
                hashtable[hash_str].append(word)
            else:
                hashtable[hash_str] = [word]

        for value in hashtable.values():
            ans.append(value)

        return ans


if __name__ == "__main__":
    sol = Solution()
    print(sol.groupAnagrams(["eat", "tea", "tan", "ate", "nat", "bat"]))