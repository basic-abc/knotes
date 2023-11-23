### ELI5
- Method to sort offline queries to answer them in an efficient rearranged order
- Sort queries according to their start (according to l) block (from squareRootDecomposition), subsequently by r
- Derive the new query value from previous query value by adding and removing elements to transform query range

### Complexity
- Time O((n + q) * sqrt(n))

q is the number of queries. Sorting all queries take O(q * log(q)).
For a single query, it could make O(n) operations. Each block may repeat this extension process, which makes it O(n * sqrt(n)).
Between any two queries, the most l can differ is O(sqrt(n)). Extended to all queries, this makes it O(sqrt(n) * q).

- Space O(q) to store the result of every query

### Application
- All queries are known beforehand and can be sorted
- Queries cannot be updated (read only, offline queries)
- If caching [l, r] can be beneficial to answering [l-1, r], [l+1, r], [l, r-1], [l, r+1]

### Implementation
```
void remove(idx);  // TODO: remove value at idx from data structure
void add(idx);     // TODO: add value at idx from data structure
int get_answer();  // TODO: extract the current answer of the data structure

int block_size;

struct Query {
    int l, r, idx;
    bool operator<(Query other) const
    {
        return make_pair(l / block_size, r) <
               make_pair(other.l / block_size, other.r);
    }
};

vector<int> mo_s_algorithm(vector<Query> queries) {
    vector<int> answers(queries.size());
    sort(queries.begin(), queries.end());

    // TODO: initialize data structure
    int cur_l = 0;
    int cur_r = -1;
    // invariant: data structure will always reflect the range [cur_l, cur_r]
    for (Query q : queries) {
        while (cur_l > q.l) {
            cur_l--;
            add(cur_l);
        }
        while (cur_r < q.r) {
            cur_r++;
            add(cur_r);
        }
        while (cur_l < q.l) {
            remove(cur_l);
            cur_l++;
        }
        while (cur_r > q.r) {
            remove(cur_r);
            cur_r--;
        }
        answers[q.idx] = get_answer();
    }
    return answers;
}
```