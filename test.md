    public static long bruteForcePowMod(long base, long exp, long mod) {
        long result = 1;
        if (mod == 1) return 0;
        for (int i = 0; i < exp; i++) {
            result = (result * base) % mod;
        }
        return result;
    }

    public static long fastPowMod(long base, long exponent, long mod) {
        if (mod == 1) return 0;  // 任何数模1都是0
        long result = 1;
        base = base % mod;  // 先取模缩小base

        while (exponent > 0) {
            // 如果当前指数为奇数，单独乘一次base
            if ((exponent & 1) == 1) {
                result = (result * base) % mod;
            }
            // 指数减半，底数平方
            exponent >>= 1;
            base = (base * base) % mod;
        }
        return result;
    }

    public class FastPowModRecursive {
        /**
         * 快速幂取模算法 (递归版)
         */
        public static long fastPowMod(long base, long exponent, long mod) {
            if (exponent == 0) return 1 % mod;
            if (mod == 1) return 0;

            long half = fastPowMod(base, exponent / 2, mod);
            long result = (half * half) % mod;

            // 如果指数为奇数，多乘一次base
            if (exponent % 2 == 1) {
                result = (result * base) % mod;
            }
            return result;
        }

        public static void main(String[] args) {
            System.out.println(fastPowMod(2, 10, 1000));  // 24
            System.out.println(fastPowMod(3, 200, 50));    // 31
        }
    }
