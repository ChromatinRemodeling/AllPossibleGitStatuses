# AllPossibleGitStatuses
Short snippet to generate all possible git statuses

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

## Result

![Pasted image 20240717171121](https://github.com/user-attachments/assets/62f6746e-3652-4b76-94d7-206f1c421fe9)

## Note

Not taking "Renamed" into consideration.
