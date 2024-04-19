"""
insert(key, value)
get(key) -> value
delete(key)
"""


class HashTable:
    def __init__(self, size) -> None:
        self.size = size
        self.create_hash_table()

    def create_hash_table(self):
        self.hash_table = [[] for _ in range(self.size)]

    """
    Insert key and value pair  into hashtable. If key already exists, update its value
    """

    def insert(self, key, value):
        hash_val = hash(key) % self.size

        bucket = self.hash_table[hash_val]

        isFound = False
        idx = -1
        for i in range(len(bucket)):
            stored_key, stored_value = bucket[i]
            if stored_key == key:
                isFound = True
                idx = i
                break

        if isFound:
            self.hash_table[hash_val][idx] = (key, value)
        else:
            self.hash_table[hash_val].append((key, value))

    """
    Given a key get its value if exists else return error message
    """

    def get(self, key):
        hash_val = hash(key) % self.size

        bucket = self.hash_table[hash_val]

        for i in range(len(bucket)):
            stored_key, stored_value = bucket[i]
            if stored_key == key:
                return stored_value

        return "Hashtable does not contain key = " + key

    """
     Takes a key and deletes it from hashtable  if it exists else prints an error message
    """

    def delete(self, key):
        hash_val = hash(key) % self.size
        bucket = self.hash_table[hash_val]

        isFound = False
        idx = -1

        for i in range(len(bucket)):
            stored_key, stored_val = bucket[i]

            if stored_key == key:
                isFound = True
                idx = i
                break

        if isFound:
            self.hash_table[hash_val].pop(idx)
        else:
            print("Entry in hashtable not found with key = " + key)


if __name__ == "__main__":
    hash_table = HashTable(10)

    hash_table.insert("Sam", 93)
    hash_table.insert("Annie", 88)

    print(hash_table.get("Annie"))

    print(hash_table.get("Harry"))

    hash_table.insert("Harry", 82)

    print(hash_table.get("Harry"))

    hash_table.delete("XYZ")

    hash_table.delete("Harry")

    print(hash_table.get("Harry"))

    print(hash_table.get("Sam"))