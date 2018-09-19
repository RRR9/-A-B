#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
 
const int BASE = 1e9;
const int BASE_LEN = 9;
  
const int SIZE = 2500;
const int MAX_SIZE = 2500;
 
void to_long(const char *str, int *val) {
    int i = strlen(str) - 1;
    int k = 0;
    while(i >= BASE_LEN - 1) {
		char tmp[BASE_LEN + 2]{};
        strncpy(tmp, str + i - (BASE_LEN - 1), BASE_LEN);
        val[k++] = atoi(tmp);
        i -= BASE_LEN;
    }
    if(i > -1) {
        char tmp[BASE_LEN + 2]{};
        strncpy(tmp, str, i + 1);
        val[k++] = atoi(tmp);
    }
	/*
	for(int j = k - 1; j >= 0; --j) {
		printf("%d ", val[j]);
	}
	printf("\n");
	*/
}
 
void addl(const int *first, const int *last, int *sum) {
    int c = 0;
    for(int i = 0; i < MAX_SIZE; ++i) {
		c = first[i] + last[i] + c;
		sum[i] = c % BASE;
		c /= BASE;
	}
}
 
void printl(const int *val) {
    int i = MAX_SIZE - 1;
    int j;
    while(!val[i] && i > 0) {
        --i;
    }
    printf("%d", val[i]);
    for(j = i - 1; j >= 0; --j) {
        int d = BASE / 10;
        while(d) {
            printf("%d", val[j] / d % 10);
            d /= 10;
        }
    }
}
 
void print_number(int n) {
    int d = BASE / 10;
    while(d) {
        printf("%d", n / d % 10);
        d /= 10;
    }
}
 
void div_by_two(int *r) {
    int i = MAX_SIZE - 1;
    int c = 0;
    bool f = false;
    while(!r[i] && i > 0) {
        --i;
    }
    for(int j = i; j >= 0; --j) {
        c = c * BASE + r[j];
        if(c < 2 && j > 0 && !f) {
            continue;
        }
        if(!f) {
            printf("%d", c / 2);
        } else {
            print_number(c / 2);
        }
        f = true;
        c %= BASE;
    }
}

void mull(const int *sum, const int *n, int *r) {
    int t = 0;
    for(int i = 0; i < MAX_SIZE; ++i) {
        for(int j = 0; j + i < MAX_SIZE ; ++j) {
            t = sum[i] * n[j] + r[i + j] + t;
            r[i + j] = t % BASE;
            t /= BASE;
        }
    }
}

void getn(const int *first, const int *last, int *n) {
	int c = 0;
	for(int i = 0; i < MAX_SIZE; ++i) {
		c = last[i] - first[i] + BASE + c;
		n[i] = c % BASE;
		c < BASE ? c = -1 : c = 0;
	}
	c = n[0] + 1;
    n[0] = c % BASE;
    if(c >= BASE) {
        c /= BASE;
        for(int i = 1; i < MAX_SIZE && c > 0; ++i) {
            c = n[i] + c;
            n[i] = c % BASE;
            c /= BASE;
        }
    }
}

int main() {
	freopen("c:\\input.txt", "rt", stdin);
	freopen("c:\\output.txt", "wt", stdout);
	int sum[MAX_SIZE]{}, n[MAX_SIZE]{}, r[MAX_SIZE]{};
	int first[MAX_SIZE]{}, last[MAX_SIZE]{};
	char s1[SIZE]{}, s2[SIZE]{};
    scanf("%s%s", s1, s2);
    to_long(s1, first);
	to_long(s2, last);
	getn(first, last, n);
	addl(first, last, sum);
    mull(sum, n, r);
    div_by_two(r);
	fclose(stdout);
	fclose(stdin);
}
