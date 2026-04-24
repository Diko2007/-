# -
СРО #2

1. Создание графа
graph = {
    "A": ["B", "C"],
    "B": ["D", "E"],
    "C": ["F"],
    "D": [],
    "E": ["F"],
    "F": []
}

2. Поиск с помощью BFS (по уровням)
from collections import deque

def bfs_search(graph, start, target):
    visited = set()
    queue = deque([start])

    while queue:
        node = queue.popleft()

        if node == target:
            return True

        if node not in visited:
            visited.add(node)
            queue.extend(graph[node])

    return False

print(bfs_search(graph, "A", "F"))  # True

3. Поиск с помощью DFS (в глубину)
def dfs_search(graph, node, target, visited=None):
    if visited is None:
        visited = set()

    if node == target:
        return True

    visited.add(node)

    for neighbor in graph[node]:
        if neighbor not in visited:
            if dfs_search(graph, neighbor, target, visited):
                return True

    return False

print(dfs_search(graph, "A", "F"))  # True

Ответы на контрольные вопросы

1. #Как граф используется в поисковых системах?

Поисковые системы представляют интернет как огромный граф:

страницы — вершины
ссылки — рёбра

Алгоритмы:

обходят страницы (краулинг)
оценивают важность (например, PageRank)

2. #Что такое обход графа?

Это процесс посещения всех вершин графа по определённому правилу.

Основные виды:

BFS (в ширину)
DFS (в глубину)
3. Чем DFS отличается от BFS?
Критерий	DFS	BFS
Принцип	идёт в глубину	идёт по уровням
Структура	стек (или рекурсия)	очередь
Путь	не гарантирует кратчайший	находит кратчайший
Использование	анализ структуры	поиск кратчайшего пути
