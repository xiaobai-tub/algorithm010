学习笔记

## quickSort
public static int partition(int[]arrays,int low,int high){
        int basic = arrays[low];
        while(low < high){
            while(low < high && basic < arrays[high]){
               high--;
            }
            arrays[low] = arrays[high];
            while(low < high && basic > arrays[low]){
                low ++;
            };
            arrays[high] = arrays[low];
        }


        arrays[low] = basic;
        return high;



    }
    public static void quickSort(int[]arrays,int low,int high){
        if(arrays.length == 0 || arrays == null) return ;
        if(high > low){
            int middle = partition(arrays,low,high);
            quickSort(arrays,low,middle - 1);
            quickSort(arrays,middle + 1,high);

        }


    }

// bubble
public static void bubble (int[] arrays){
        for(int i = 0;i < arrays.length - 1;i++){
            for(int j = 0;j < arrays.length - i - 1;j++){
                if(arrays[j] > arrays[j+1]){
                    int temp = arrays[j];
                    arrays[j] = arrays[j+1];
                    arrays[j+1] = temp;
                }
            }
        }
    }
	
//归并
   public static void merge(int[] array,int low,int high){
        if(low >= high || array == null) return;
        int middle = (low + high) >> 1;
        merge(array,low,middle);
        merge(array,middle + 1,high);
        mergeArray(array,low,middle,high);

    }
	
	   public static void mergeArray(int[] array,int low,int middle,int high) {
        int[] temp = new int[high-low+1];
        int k = 0;
        int p = low;
        int q = middle + 1;
        while(p <= middle && q <= high){
                temp[k++] = array[p] <= array[q]?array[p++]:array[q++];
        }
        while(p <= middle) temp[k++] = array[p++];

        while(q <= high) temp[k++] = array[q++];


        for(int i = 0;i < temp.length;i++){
            array[low+i] = temp[i];
        }
        
    }
//堆排序
static void heapify(int[] array, int length, int i) {

        int left = 2 * i + 1, right = 2 * i + 2;
        int largest = i;
        if (left < length && array[left] > array[largest]) {
            largest = left;
        }
        if (right < length && array[right] > array[largest]) {
            largest = right;
        }
        if (largest != i) {
            int temp = array[i]; array[i] = array[largest]; array[largest] = temp;
            heapify(array, length, largest);
        }
    }


    public static void heapSort(int[] array) {
        if(array == null) return;
        int length = array.length;
		
		//从最后一个节点的父节点开始校验堆的结构
        for(int i = (length-1)/2 ;i >= 0;i--){
            heapify(array,length,i);
        }
        for(int i = length - 1 ;i >= 0;i--){
            int temp = array[0];
            array[0] = array[i];
            array[i] = temp;
            heapify(array,i,0);
        }

    }