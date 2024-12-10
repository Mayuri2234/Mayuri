1. We are given two arrays that represent the arrival and departure time of trains.The task is to find the minimum number of platforms requires so that no train need to wait.
   import java.util.Arrays;

 class Main {
    public static int findMinPlatforms(int[] arrival, int[] departure) {
        
        Arrays.sort(arrival);
        Arrays.sort(departure);

        int n = arrival.length;
        int platformsNeeded = 0, maxPlatforms = 0;

        int i = 0, j = 0;

        while (i < n && j < n) {
            if (arrival[i] < departure[j]) {
                
                platformsNeeded++;
                i++;
            
                maxPlatforms = Math.max(maxPlatforms, platformsNeeded);
            } else {
                
                platformsNeeded--;
                j++;
            }
        }

        return maxPlatforms;
    }

    public static void main(String[] args) {
        int[] arrival = {900, 940, 950, 1100, 1500, 1800};
        int[] departure = {910, 1200, 1120, 1130, 1900, 2000};

        System.out.println("Minimum platforms required: " + findMinPlatforms(arrival, departure));
    }
}
