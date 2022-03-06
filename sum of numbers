#include <bits/stdc++.h>
using namespace std;
#define ll long long
#define N 100005
#define MOD 1000000007
#define dd double
#define vi vector<int>
#define vll vector<ll>
#define forr(i, n) for(int i = 0; i < n; i++)
#define REP(i,a,b) for(int i=a;i<b;i++)
#define rep1(i,b) for(int i=1;i<=b;i++)
#define pb push_back
#define mp make_pair
#define clr(x) x.clear()
#define sz(x) ((int)(x).size())
#define ms(s, n) memset(s, n, sizeof(s))
#define F first
#define S second
#define all(v) v.begin(),v.end()
#define rall(v) v.rbegin(),v.rend()
#define int ll
ll po(ll a, ll x, ll m) { if (x == 0) {return 1;} ll ans = 1; ll k = 1;  while (k <= x) {if (x & k) {ans = ((ans * a) % m);} k <<= 1; a *= a; a %= m; } return ans; }
int query(int *tree, int index, int s, int e, int qs, int qe) {

 if (qs > e || qe < s) {
  return 1e18;
 }

 if (qs <= s && qe >= e) {
  return tree[index];
 }


 int mid = (s + e) / 2;
 int leftAns = query(tree, 2 * index, s, mid, qs, qe);
 int rightAns = query(tree, 2 * index + 1, mid + 1, e, qs, qe);

 return min(leftAns, rightAns);
}
void updateNode(int *tree, int index, int s, int e, int i, int inc) {
 if (i < s || i > e) {
  return;
 }
 if (s == e) {
  tree[index] += inc;
  return;
 }
 int mid = (s + e) / 2;
 updateNode(tree, 2 * index, s, mid, i, inc);
 updateNode(tree, 2 * index + 1, mid + 1, e, i, inc);
 tree[index] = min(tree[2 * index], tree[2 * index + 1]);
 return;
}
void buildTree(int *tree, int *a, int index, int s, int e) {

 if (s == e) {
  tree[index] = a[s];
  return;
 }
 if (s > e) {
  return;
 }


 int mid = (s + e) / 2;
 buildTree(tree, a, 2 * index, s, mid);
 buildTree(tree, a, 2 * index + 1, mid + 1, e);
 tree[index] = min(tree[2 * index], tree[2 * index + 1]);
}

int32_t main() {
 ios_base::sync_with_stdio(false);
 cin.tie(NULL);
 cout.tie(NULL);

 int n, w, d;
 cin >> n >> w >> d;
 if (n == 0) {
  cout << "Both are right";
  return 0;
 }
 int a[n];
 forr(i, n) {
  cin >> a[i];
 }
 int dp2[n];
 int tot = 0;
 forr(i, n) {
  dp2[i] = a[i];
  tot += a[i];
 }
 int t[4 * n + 1];
 //ms(t, 0);
 buildTree(t, a, 1, 0, n - 1);
 //cout << query(t, 1, 0, n - 1, 4, n - 2) << "\n";
 int k = w + 1;



 for (int i = k; i < n; i++) {
  int qs = query(t, 1, 0, n - 1, i - k, i - 1);

  updateNode(t, 1, 0, n - 1, i, qs);
 }
 int ans1;
 if (k <= n)
  ans1 = query(t, 1, 0, n - 1, n  - k, n - 1);
 else
  ans1 = 0;
 k  = w + d + 1;
 int t2[4 * n + 1];
 buildTree(t2, a, 1, 0, n - 1);
 for (int i = k; i < n; i++) {
  //cout << i - k << " " << i - 1 << "\n";
  int qs = query(t2, 1, 0, n - 1, i - k, i - 1);
  //dp2[i] += qs;
  updateNode(t2, 1, 0, n - 1, i, qs);
 }
 int ans2;
 if (k <= n)
  ans2 = query(t2, 1, 0, n - 1, n  - k, n - 1);
 else
  ans2 = 0 ;
 //cout << ans1 << " " << ans2 << "\n";
 ans1  = tot - ans1;
 ans2 = tot - ans2;
 //cout << ans1 << " " << ans2 << "\n";
 int ans  = abs(ans1 - ans2);
 if (ans1 > ans2) {
  cout << "Wrong " << ans << "\n";
 } else if (ans2 > ans1) {
  cout << "Right " << ans << "\n";
 } else {
  cout << "Both are right";
 }
 return 0;
}
