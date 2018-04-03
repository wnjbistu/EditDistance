# EditDistance
//字符串之间编辑距离。给定两个字符串s1和s2，两者的编辑距离定义为将s1转换为s2的最小编辑操作数（等价于将s2转换为s1的最小编辑操作数）。  编辑操作有3种：插入一个字符、删除一个字符、替换一个字符。
package common;

import org.junit.Assert;

public class LevenshteinDistance {

    public static int getDistance(String src, String des) {
        int[][] m=new int[des.length()+1][];

        for (int i = 0; i < m.length; i++) {
            m[i]=new int[src.length()+1];
        }

        for(int i=0;i<src.length()+1;i++){
            m[0][i]=i;
        }

        for(int i=0;i<des.length()+1;i++){
            m[i][0]=i;
        }

        for(int i=1;i<des.length()+1;i++){
            for (int j = 1; j < src.length()+1; j++) {
                int rcost=des.charAt(i-1)==src.charAt(j-1)?0:1;
                m[i][j]=Math.min(Math.min(m[i-1][j]+1, m[i-1][j-1]+rcost), m[i][j-1]+1);
            }
        }

        return m[des.length()][src.length()];
    }

    public static void main(String[] args) {
        int num = 0;
        String str1 = "halo,交个朋友吗？这个不长在线，签名栏有连系方式噢";
        String str2 ="哈喽啊，交个朋友可以不？这不常在，我签名栏里有我的联系方法O";
        String str3 ="你好啊，认识一下啊！！这里不常在的，签名栏有我联系方式噢";
        String str4 ="你好!不考虑互粉一下吗？哈哈，我不常在线，我签名栏有我联系访式噢";
        String str5 ="hi，交个朋友？不经常上这个，签名栏有我联系方试";
        String str6 ="哈喽哈喽！很高兴认识你，LESPARK不总上，签名栏有我联希方式哈";
        String str7 ="hi，交个朋友？不经常上，签名栏有我联系方试";
        String str8 ="hello，认识一下吗我不总上这个，签名栏有联系方是。";
        String str9 ="哈喽哈喽！很高兴认识你，我不总上，签名栏有我联希方式哈";
        String str10 ="123";
        String str11 ="222";
        num = getDistance(str10,str11);
        System.out.print(num);
    }

}
