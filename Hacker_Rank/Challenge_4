from queue import PriorityQueue

# Function to perform UCS
def ucs(grid, start, end):
    rows, cols = len(grid), len(grid[0])
    visited = set()
    parent = {}
    cost = {}

    pq = PriorityQueue()
    pq.put((0, start))

    while not pq.empty():
        current_cost, current_node = pq.get()

        if current_node == end:
            break

        if current_node in visited:
            continue

        visited.add(current_node)

        r, c = current_node
        neighbors = [(r - 1, c), (r + 1, c), (r, c - 1), (r, c + 1)]

        for neighbor in neighbors:
            nr, nc = neighbor

            if 0 <= nr < rows and 0 <= nc < cols and grid[nr][nc] != '%':
                new_cost = current_cost + (1 if grid[nr][nc] != '.' else 0)

                if neighbor not in cost or new_cost < cost[neighbor]:
                    cost[neighbor] = new_cost
                    pq.put((new_cost, neighbor))
                    parent[neighbor] = current_node

    # Reconstruct the path
    path = []
    current_node = end
    while current_node != start:
        path.append(current_node)
        current_node = parent[current_node]
    path.append(start)
    path.reverse()

    return path, cost[end]

# Read input
pacman = tuple(map(int, input().split()))
food = tuple(map(int, input().split()))
rows, cols = map(int, input().split())
grid = [list(input().strip()) for _ in range(rows)]

# Perform UCS
path, distance = ucs(grid, pacman, food)

# Print the results
print(distance)
for node in path:
    print(node[0], node[1])
