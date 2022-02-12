# Simple-Blockchain-Implementation-in-Python-Programming-Language
#Govind project work for jetking hackathon

import hashlib
def hashGenerator(data):
    new_result= hashlib.sha256(data.encode())
    return new_result.hexdigest()

class Block:
    def __init__(self, data, hash, prev_hash):
        self.data = data
        self.hash = hash
        self.prev_hash = prev_hash

class Blockchain:
    def __init__(self):
        hashLast = hashGenerator('Hash of the last Block')
        hashStart = hashGenerator('Hash of the current Block')
        genesis = Block('First Block of the Blockchain',
                        hashStart, hashLast)
        self.chain = [genesis]

    def add_block(self, data):
        prev_hash = self.chain[-1].hash
        hash = hashGenerator(data+prev_hash)
        block = Block(data, hash, prev_hash)
        self.chain.append(block)

bc = Blockchain()
bc.add_block('I am the Second Block of blockchain')
bc.add_block('I am the third Block of blockchain')
bc.add_block('I am the fourth Block of blockchain')
bc.add_block('I am the fifth Block of blockchain')
bc.add_block('I am the Sixth Block of blockchain')

for blocks in bc.chain:
    print("List of the Blocks Information", blocks.__dict__)
