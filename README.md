# AllPossibleGitStatuses
Short snippet to generate all possible git file statuses

(TODO: consider merging and rebasing)

## Steps

1. initialize a new git repo, `cd` into it
2. run the following code
(Should work on Linux/MacOS/Windows PowerShell)

```
echo D_1 > D_.txt
echo AD1 > AD.txt
echo MD1 > MD.txt
echo _D1 > _D.txt
echo _Q1 > _Q.txt
echo DQ1 > DQ.txt

echo AM1 > AM.txt
echo A_1 > A_.txt
echo M_1 > M_.txt
echo _M1 > _M.txt
echo MM1 > MM.txt

git add D_.txt MD.txt _D.txt DQ.txt M_.txt _M.txt MM.txt
git commit -m "111111"
git rm *
rm ./*.txt

echo AD1 > AD.txt
echo MD2 > MD.txt
echo _D1 > _D.txt
echo AM1 > AM.txt
echo A_1 > A_.txt
echo M_2 > M_.txt
echo _M1 > _M.txt
echo MM2 > MM.txt

git add *
rm ./*.txt

echo _Q1 > _Q.txt
echo DQ1 > DQ.txt
echo AM2 > AM.txt
echo A_1 > A_.txt
echo M_2 > M_.txt
echo _M2 > _M.txt
echo MM1 > MM.txt
```

3. run `git status -s`

A clearer view of the current content of the git repo:

|  Filename (.txt)  | Working directory/tree | Staging area (index) | .git directory (Repository) |     
| --- | ---------------------- | -------------------- | --------------------------- | 
| D\_ |                        |                      | D\_1                        |     
| AD  |                        | AD1                  |                             |     
| MD  |                        | MD2                  | MD1                         |    
| \_D |                        | \_D1                 | \_D1                        |     
| \_Q | \_Q1                   |                      |                             |     
| DQ  | DQ1                    |                      | DQ1                         |     
| AM  | AM2                    | AM1                  |                             |     
| A\_ | A\_1                   | A\_1                 |                             |     
| M\_ | M\_2                   | M\_2                 | M\_1                        |     
| \_M | \_M2                   | \_M1                 | \_M1                        |     
| MM  | MM1                    | MM2                  | MM1                         |     

## Result

![Pasted image 20240717171121](https://github.com/user-attachments/assets/62f6746e-3652-4b76-94d7-206f1c421fe9)

## Note

Not taking "Renamed" into consideration.

## Analysis


The left (green) column of the statuses shows the difference between the staging area and the repo. Possible combinations:

(D, A and M stands for Deleted, Added and Modified, respectively. \_ means there are no additions, deletions and modifications, and can be understood as a no-status. \_/M stands for no-status or Modified, depending on whether `a` is the same in the repo and in the staging area.)

| Status of file `a`              | `a` exists in the repo? | N   | Y    |
| ------------------------------- | ----------------------- | --- | ---- |
| `a` exists in the staging area? |                         |     |      |
| N                               |                         | \_  | D    |
| Y                               |                         | A   | \_/M |

The right (red) column of the statuses shows the difference between the working directory and the staging area. Possible combinations:

(?? stands for Untracked.)

| Status of file `a`                   | `a` exists in the staging area? | N   | Y    |
| ------------------------------------ | ------------------------------- | --- | ---- |
| `a` exists in the working directory? |                                 |     |      |
| N                                    |                                 | \_  | D    |
| Y                                    |                                 | ??  | \_/M |

Putting all the possible combinations of the left and right statuses together, we get 11 statuses as shown above.

