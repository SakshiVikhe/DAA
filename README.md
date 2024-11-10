# DAA
# Get user input
n = int(input("Enter the number of items: "))
values = []
weights = []

for i in range(n):
    value = int(input(f"Enter the value of item {i + 1}: "))
    weight = int(input(f"Enter the weight of item {i + 1}: "))
    values.append(value)
    weights.append(weight)

capacity = int(input("Enter the capacity of the knapsack: "))

# Dynamic programming array initialization
dp = [[0 for _ in range(capacity + 1)] for _ in range(n + 1)]

# Build the DP table
for i in range(1, n + 1):
    for w in range(capacity + 1):
        if weights[i - 1] <= w:
            dp[i][w] = max(dp[i - 1][w], dp[i - 1][w - weights[i - 1]] + values[i - 1])
        else:
            dp[i][w] = dp[i - 1][w]

# Output the result
print("Maximum value in knapsack:", dp[n][capacity])
