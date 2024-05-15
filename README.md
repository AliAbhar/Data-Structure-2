python 
class DoubleEndedQueue: 
 def __init__(self, max_size): 
 self.max_size = max_size 
 self.Q = [0] * max_size 
 self.num = 0 
 self.first = 0 
 
 def push_back(self, item): # Like one-way queue 
 if self.num >= self.max_size: 
 raise Exception("Queue overflow") 
 self.Q[(self.num + self.first) % self.max_size] = item 
 self.num += 1 
 def push_front(self, item): # New 
 if self.num >= self.max_size: 
 raise Exception("Queue overflow") 
 self.first = (self.first - 1) % self.max_size 
 self.Q[self.first] = item 
 self.num += 1 
 def pop_front(self): # Like one-way queue 
 if self.num == 0: 
 raise Exception("Queue empty") 
 item = self.Q[self.first] 
 self.first = (self.first + 1) % self.max_size 
 self.num -= 1 
 return item 
 
 def front(self): # Like one-way queue 
 if self.num == 0: 
 raise Exception("Queue empty") 
 return self.Q[self.first] 
 
 def pop_back(self): # New 
 if self.num == 0: 
 raise Exception("Queue empty") 
 self.num -= 1 
 return self.Q[(self.num + self.first) % self.max_size] 
 
 def back(self): # New 
 if self.num == 0: 
 raise Exception("Queue empty") 
 return self.Q[(self.num + self.first - 1) % self.max_size] 
 
 def is_empty(self): 
 return self.num == 0 
 
 def size(self): 
 return self.num 
 
 def is_full(self): 
 return self.num >= self.max_size
