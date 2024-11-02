# Total-Poison-Time

In a legendary battle, the mighty warrior Alex is using poison attacks to weaken his enemy, Leo. Each time Alex strikes, Leo becomes poisoned for a specific duration of seconds. If Alex launches a new attack before the poison from the previous one wears off, the poison's timer resets, and Leo remains poisoned for the full duration starting from the latest attack.
You are given a list called timeSeries, where each element represents the exact second Alex attacks Leo, and an integer duration, which tells how long each poison effect lasts. Your mission is to calculate the total number of seconds Leo remains poisoned during the entire battle. Can you help Alex track the full effect of his poison on Leo?

def total_poison_time(timeSeries, duration):
    if not timeSeries:
        return 0
    
    total_time = 0
    
    for i in range(len(timeSeries) - 1):
        interval = timeSeries[i + 1] - timeSeries[i]
        
        if interval >= duration:
            total_time += duration
        else:
            total_time += interval
    
    total_time += duration
    
    return total_time

n = int(input().strip())
timeSeries = list(map(int, input().strip().split()))
duration = int(input().strip())

print(total_poison_time(timeSeries, duration))
