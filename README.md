 package com.ccdx.test;

import com.ccdx.array.Array;

public class MethodTest {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Array<Integer> arr=new Array<Integer>();
		for(int i=0;i<10;i++)
		  arr.addLast(i);
		
		 /* arr.addLast(10);
		  arr.addLast(11);
		  arr.addLast(12);*/
		 /* System.out.println(arr.toString());
		  arr.remove(2);	  
		  System.out.println(arr.toString());*/
		  arr.removeElement(5);
		  arr.removeElement(6);
		  arr.removeElement(4);
		  arr.removeElement(2);
		  arr.removeElement(1);
		  System.out.println(arr.toString());
	}
}
