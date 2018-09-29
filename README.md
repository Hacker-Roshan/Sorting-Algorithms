/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package sortingarraydemo;
import java.util.Scanner;
/**
 *
 * @author hacker
 */
public class SortingArrayDemo {

    void PrintArray(int arr[])
    {
        int n=arr.length;
        for(int i=1;i<n;i++)
        {
            System.out.print(arr[i]+"  ");
            
        }
        System.out.println();
    }
    void SelectionSort(int arr[])
    {
        int n=arr.length;
        for(int i=0;i<n-1;i++)
        {
            int min=i;
            for(int j=i+1;j<n;j++)
                if(arr[j]<arr[min])
                    min=j;
            int temp=arr[min];
            arr[min]=arr[i];
            arr[i]=temp;
        }
    }
    void MergeSort(int arr[],int l,int m,int r)
    {
        int n1=m-l+1;
        int n2=r-m;
        int L[]=new int [n1];
        int R[]=new int [n2];
        for(int i=0;i<n1;++i)
            L[i]=arr[l+i];
        for(int j=0;j<n2;++j)
            R[j]=arr[m+1+j];
        
        int i=0,j=0;
        int k=l;
        while (i<n1 && j<n2)
        {
            if(L[i]<=R[j])
            {
                arr[k]=L[i];
                i++;
            }
            else
            {
                arr[k]=R[j];
                j++;
            }
            k++;
        }
        while(i<n1)
        {
            arr[k]=L[i];
            i++;
            k++;
            
        }
        while(j<n2)
        {
            arr[k]=R[j];
            j++;
            k++;
          
        }
    }
    void MergeSorting(int arr[],int l,int r)
    {
        if(l<r)
        {
            int m=(l+r)/2;
            MergeSorting(arr,l,m);
            MergeSorting(arr,m+1,r);
            MergeSort(arr,l,m,r);
                    
        }
    }
    
    void InsertionSort(int arr[])
    {
        int n=arr.length;
        for(int i=1;i<n;i++)
        {
            int key=arr[i];
            int j=i-1;
            while(j>=0 && arr[j]>key)
            {
                arr[j+1]=arr[j];
                j=j-1;
                
            }
            arr[j+1]=key;
        }
    }
    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        // TODO code application logic here
        int[] arr=new int[1500000];
        
        
        Scanner sc=new Scanner(System.in);
        System.out.println(" 1-Selection Sort\n 2-Merge Sort\n 3-Insertion Sort\nEnter Your Choice");
        int n=sc.nextInt();
        System.out.println("Enter Total Number of Elements");
        int x=sc.nextInt();
        for(int i=0;i<=x;i++)
            {
                arr[i]=i;
            }
        switch(n)
        {
            case 1:
                SortingArrayDemo obj=new SortingArrayDemo();
                obj.SelectionSort(arr);
                System.out.println("Selection Sort :");
                obj.PrintArray(arr);
                break;
                
            case 2:
                SortingArrayDemo obj1=new SortingArrayDemo();
                obj1.MergeSorting(arr,0,arr.length-1);
                System.out.println("Merge Sort :");
                obj1.PrintArray(arr);
                break;
            
            case 3:
                SortingArrayDemo obj2=new SortingArrayDemo();
                obj2.InsertionSort(arr);
                System.out.println("Insertion Sort :");
                obj2.PrintArray(arr);
                break;
        }
    }
    
}

