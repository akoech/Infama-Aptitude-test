# Infama-Aptitude-test
 static bool hasArrayTwoMovies(int[] movieDuration, int lengthOfFlight)
        {
            int l, r;
            int arr_size= movieDuration.Count();
            /* Sort the elements */
            sort(movieDuration, 0, arr_size - 1);

            /* Now look for the two durations
            in the sorted array*/
            l = 0;
            r = arr_size - 1;
            while (l < r)
            {
                if (movieDuration[l] + movieDuration[r] == lengthOfFlight)
                    return true;
                else if (movieDuration[l] + movieDuration[r] < lengthOfFlight)
                    l++;
                else
                    r--;
            }
            return false;
        }

       
        static int partition(int[] arr, int low, int high)
        {
            int pivot = arr[high];
           
            int i = (low - 1);
            for (int j = low; j <= high - 1; j++)
            {
                if (arr[j] <= pivot)
                {
                    i++;
                   
                    int temp = arr[i];
                    arr[i] = arr[j];
                    arr[j] = temp;
                }
            }
           
            int temp1 = arr[i + 1];
            arr[i + 1] = arr[high];
            arr[high] = temp1;

            return i + 1;
        }
       
        static void sort(int[] arr, int low, int high)
        {
            if (low < high)
            {
                int pi = partition(arr, low, high);
               
                sort(arr, low, pi - 1);
                sort(arr, pi + 1, high);
            }
        }
