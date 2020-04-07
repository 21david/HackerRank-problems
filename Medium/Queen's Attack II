/*
https://www.hackerrank.com/challenges/queens-attack-2/problem
*/

import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;

public class Solution {

    // Complete the queensAttack function below.
    static int queensAttack(int n, int k, int r_q, int c_q, int[][] obstaclesArray) {
        HashSet<String> obstacles = new HashSet<>();

        // because of 0 based indexing
        r_q--;
        c_q--;

        String hash = "";
        for(int[] obstacle : obstaclesArray)
        {
            hash = (obstacle[0]  - 1) + "#" + (obstacle[1] - 1);
            obstacles.add(hash);
        }

        // attempt to go in all 8 directions
        int attacked = 0;

        int[] offsets = {-1, 0, 1};

        for(int i = 0; i < 3; i++)
            for(int j = 0; j < 3; j++)
            {
                if(j == 1 && i == 1)
                    continue;
                
                attacked += attack(obstacles, r_q, c_q, n, offsets[i], offsets[j]);
            }

        return attacked;
    }

    public static int attack(HashSet<String> obstacles, int r_q, int c_q, int n, int ro, int co)
    {
        int count = 0;

        r_q += ro;
        c_q += co;

        while(inBounds(n, r_q, c_q))
        {
            if(obstacles.contains(r_q + "#" + c_q))
                return count;
            
            count++;
            r_q += ro;
            c_q += co;
        }

        return count;
    }

    public static boolean inBounds(int n, int r, int c)
    {
        return r >= 0 && c >= 0 && r < n && c < n;
    }

    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) throws IOException {
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        String[] nk = scanner.nextLine().split(" ");

        int n = Integer.parseInt(nk[0]);

        int k = Integer.parseInt(nk[1]);

        String[] r_qC_q = scanner.nextLine().split(" ");

        int r_q = Integer.parseInt(r_qC_q[0]);

        int c_q = Integer.parseInt(r_qC_q[1]);

        int[][] obstacles = new int[k][2];

        for (int i = 0; i < k; i++) {
            String[] obstaclesRowItems = scanner.nextLine().split(" ");
            scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

            for (int j = 0; j < 2; j++) {
                int obstaclesItem = Integer.parseInt(obstaclesRowItems[j]);
                obstacles[i][j] = obstaclesItem;
            }
        }

        int result = queensAttack(n, k, r_q, c_q, obstacles);

        bufferedWriter.write(String.valueOf(result));
        bufferedWriter.newLine();

        bufferedWriter.close();

        scanner.close();
    }
}
