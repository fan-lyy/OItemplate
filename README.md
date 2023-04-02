# OItemplate
```cpp
#include<bits/stdc++.h>
using namespace std;
#define maxn 100005
#define reg register  
#define ll long long
#define ull unsigned long long 
#define fio(in,out) freopen(in,"r",stdin),freopen(out,"w",stdout)
namespace fast
{
	template<class T>
	inline T Read()
	{
	    T res=0,f=1;char c;
	    for(;(c=getchar())<'0' || c>'9';c=='-'?f=-f:0);
	    while(c>='0' && c<='9')res=(res<<3)+(res<<1)+c-'0',c=getchar();
	    return res*f;
	}
	inline int read(){return Read<int>();}
	inline char getchr()
	{
		char c;
		while(c==' ' || c=='\n')
	        c=getchar();
	    return c;
	}
	inline string getstr()
	{
	    string s;char c=getchar();
	    while((c<'a' || c>'z') && (c<'A' || c>'Z') && (c<'0' || c>'9'))
	        c=getchar();
	    while((c>='a' && c<='z') || (c>='A' && c<='Z') || (c>='0' && c<='9'))
	        s+=c,c=getchar();
	    return s;
	}
}
namespace tmath
{
	ll s[maxn],sv[maxn];
	inline int qpow(int base,int x)
	{
		int ans=1;
		while(x)
		{
			if(x&1)ans*=base;
			base*=base;
			x>>=1;
		}
		return ans;
	}
	inline int qpow(int base,int x,int mod)
	{
		int ans=1;
		while(x)
		{
			if(x&1)ans=(ans*base)%mod;
			base=(base*base)%mod;
			x>>=1;
		}
		return ans;
	}
	inline ll qpow(ll base,ll x)
	{
		ll ans=1;
		while(x)
		{
			if(x&1)ans*=base;
			base*=base;
			x>>=1;
		}
		return ans;
	}
	inline ll qpow(ll base,ll x,ll mod)
	{
		ll ans=1;
		while(x)
		{
			if(x&1)ans=(ans*base)%mod;
			base=(base*base)%mod;
			x>>=1;
		}
		return ans;
	}
	template<class T>
	inline void exgcd(T a,T b,T &x,T &y)
	{
		if(b==0){x=1,y=0;return;}
		exgcd(b,a%b,x,y);
		T t=x;x=y;y=t-(b/a)*y;
	}
	inline void prim(int n,int *(&d),int &tot,bitset<maxn> &vis)
	{
		vis.reset();vis[0]=vis[1]=1;
		for(int i=2;i<=n;i++)
			if(!vis[i])
			{
				d[++tot]=i;
				for(int j=2;j*i<=n;j++)vis[i*j]=1;
			}
	}
	inline void inverse(int n,ll *(&inv),ll mod)
	{
		inv[1]=1;
		for(int i=2;i<=n;i++)
			inv[i]=(ll)(mod-mod/i)*inv[mod%i]%mod;
	}
	inline void inverse(int n,ll *(&inv),ll mod,ll *a)
	{
		s[0]=1;
		for(int i=1;i<=n;i++)s[i]=s[i]*a[i]%mod;
		sv[n]=qpow(s[n],mod-2,mod);
		for(int i=n;i>=1;i--)sv[i-1]=sv[i]*a[i]%mod;
		for(int i=1;i<=n;i++)inv[i]=sv[i]*s[i-1]%mod;
	}
}
namespace graph
{
	int head[maxn],nxt[maxn*2],to[maxn*2],w[maxn*2],tot;
	inline void add(int u,int v)
	{
		to[++tot]=v;
		nxt[tot]=head[u];
		head[u]=tot;
	}
	inline void add(int u,int v,int dis)
	{
		to[++tot]=v;
		nxt[tot]=head[u];
		head[u]=tot;
		w[tot]=dis;
	}
}
namespace datastruct
{
	template<class T>
	struct treearray
	{
    	T tre[maxn],kk;
    	T lwbt(T x){return x&(-x);}
    	T ask(T i){T ans=0; for(;i;i-=lwbt(i))ans+=tre[i];return ans;}
    	void add(T i,T k){for(;i<=kk;i+=lwbt(i))tre[i]+=k;}
	};
	#ifdef datasqrt 
		int id[maxn],l[maxn],r[maxn];
		inline void init(int n)
		{
			reg int len,tot;
			len=sqrt(n);tot=n/len;
			if(n%len)tot++;
			for(i=1;i<=n;i++)id[i]=(i-1)/len+1;
			for(i=1;i<=tot;i++)l[i]=(i-1)*len+1,r[i]=i*len;r[tot]=n;
		}  
	#endif
} 
```
