# OS-EX.8-IMPLEMENTATION-OF-BANKER-S-ALGORITHM

# AIM

To write a C program to implement Bankers Algorithm.

# ALGORITHM

1: Get the no of processes.

2: Get the process numbers.

3: Get the no of resources types and instances of it.

4: Get Max demand of each process of n x m matrices.

5: Get the n x m matrices the number of resources of each type currently allocated to each process.


6: Calculate the n x m of the remaining resource need of each process.

7: Initialize work as available resource and array of finish to false.

8: Check the Needed resource is lesser than the available resource if not display the System not in safe state and if it is lesser than system in safe state.

9: Initialize work as sum of work and allocation, check if array of finish is true go to step 7 again if not go to step 8.

10: Check that request can be immediately granted.

11: If single request is lesser than or equal to available if true means arrive to new state.

12: Print the sequence if it is in safe state or print not in safe state.

# PROGRAM
```
#include <stdio.h>
int main()
{

	int n, m, i, j, k;
	n = 5; // Number of processes
	m = 3; // 
	int alloc[5][3] = { { 0, 1, 0 }, // P0 // Allocation Matrix
						{ 2, 0, 0 }, // P1
						{ 3, 0, 2 }, // P2
						{ 2, 1, 1 }, // P3
						{ 0, 0, 2 } }; // P4

	int max[5][3] = { { 7, 5, 3 }, // P0 // MAX Matrix
					{ 3, 2, 2 }, // P1
					{ 9, 0, 2 }, // P2
					{ 2, 2, 2 }, // P3
					{ 4, 3, 3 } }; // P4

	int avail[3] = { 3, 3, 2 }; // Available Resources

	int f[n], ans[n], ind = 0;
	for (k = 0; k < n; k++) {
		f[k] = 0;
	}
	int need[n][m];
	for (i = 0; i < n; i++) {
		for (j = 0; j < m; j++)
			need[i][j] = max[i][j] - alloc[i][j];
	}
	int y = 0;
	for (k = 0; k < 5; k++) {
		for (i = 0; i < n; i++) {
			if (f[i] == 0) {

				int flag = 0;
				for (j = 0; j < m; j++) {
					if (need[i][j] > avail[j]){
						flag = 1;
						break;
					}
				}

				if (flag == 0) {
					ans[ind++] = i;
					for (y = 0; y < m; y++)
						avail[y] += alloc[i][y];
					f[i] = 1;
				}
			}
		}
	}

	int flag = 1;
	
	for(int i=0;i<n;i++)
	{
	if(f[i]==0)
	{
		flag=0;
		printf("The following system is not safe");
		break;
	}
	}
	
	if(flag==1)
	{
	printf("Following is the SAFE Sequence\n");
	for (i = 0; i < n - 1; i++)
		printf(" P%d ->", ans[i]);
	printf(" P%d", ans[n - 1]);
	}
	

	return (0);
}
```
# OUTPUT

![image](https://github.com/Harsayazheni/OS-EX.8-IMPLEMENTATION-OF-BANKER-S-ALGORITHM/assets/118708467/16bca875-09fd-4ea8-8399-03df2cfefea2)

# RESULT

Thus, implement Bankers Algorithm to avoid Deadlock is implemented successfully using C program.
