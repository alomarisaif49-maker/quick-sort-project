import random
class Quick_sort:
         def __init__(self,arr):
            self.arr=arr.copy()
            self.swaps=0


         def quick_sort(self,start,end,partition_func):
            if start<end:
             pi=partition_func(self,start,end) #pivot
             self.quick_sort(start,pi-1,partition_func)  #هونبدي ارتب الي اصغر من pivot
             self.quick_sort(pi+1,end,partition_func)    #هونبدي ارتب الي الكبر من pivot

         def partition (self,start,end):
          pivot=self.arr[start]
          i=start+1
          for j in range(start+1,end+1):
               if self.arr[j]<=pivot:
                    self.arr[i],self.arr[j]=self.arr[j],self.arr[i]
                    i+=1
                    self.swaps+=1
          self.arr[start],self.arr[i-1]=self.arr[i-1],self.arr[start]
          self.swaps+=1
          return i-1
         
         def partiton_last(self,start,end):
             pivot=self.arr[end]
             i=start-1
             for j in range (start,end):
                 if self.arr[j]<=pivot:
                     self.arr[i],self.arr[j]=self.arr[j],self.arr[i]
                     i+=1
                     self.swaps+=1
             self.arr[i+1],self.arr[end]=self.arr[end],self.arr[i+1]
             self.swaps+=1
             return i+1
         def partitin_random(self,start,end):
            rand_index=random.randint(start, end)
            self.arr[start],self.arr[rand_index]=self.arr[rand_index],self.arr[start]
            self.swaps+=1
            pivot=self.arr[start]
            i=start+1
            for j in range(start+1,end+1):
                if self.arr[j]<=pivot:
                  self.arr[i],self.arr[j]=self.arr[j],self.arr[i]
                  i+=1
                  self.swaps+=1
            self.arr[i-1],self.arr[start]=self.arr[start],self.arr[i-1]
            self.swaps+=1
            return i-1
         def generate_data(size,case_type):
             if case_type=="sorted":
                 return list(range(size))
             elif case_type=="reversed":
                 return list(range(size,0,-1))
             elif case_type=="random":
                 return [random.randint(0,size) for i in range(size)]
arr = Quick_sort.generate_data(10, "random")

qs = Quick_sort(arr)
qs.quick_sort(0, len(arr)-1, Quick_sort.partition)

print(qs.arr)
print("swaps:", qs.swaps)
