package com.ccdx.array;

public class Array<E> {
	private E[] data;
	private int size;

	// 有参构造
	public Array(int capacity) {
		data = (E[])(new Object[capacity]);
		size = 0;
	}

	// 无参构造，调用有参构造方法，默认最大容量为10
	public Array() {
		this(10);
	}

	// 数组长度
	public int getSize() {
		return size;
	}

	// 数组最大容量
	public int getCapacity() {
		return data.length;
	}

	// 判断数组是否为空
	public boolean isEmpty() {
		return size == 0;
	}

	// 向所有数组前面添加元素
	public void addFirst(E e) {
		add(0, e);
	}

	// 向数组末尾当中添加元素
	public void addLast(E e) {
		add(size, e);
	}

	// 向指定位置插入元素
	public void add(int index, E e) {
		if (index < 0 || index > size)
			throw new IllegalArgumentException("index requires >0 and <=size");
		if (size == data.length)
			resize(2*data.length);
		for (int i = size - 1; i >= index; i--) {
			data[i + 1] = data[i];
		}
		data[index] = e;
		size++;
	}
	private void resize(int newCapacity) {
		// TODO Auto-generated method stub
		E[] newData=(E[])new Object[newCapacity];
		for(int i=0;i<size;i++)
			newData[i]=data[i];
		data=newData;
		
	}

	//获得数组中的元素
	public E get(int index) {
		if(index<0||index>=size)
			throw new IllegalArgumentException("数组下标错误");
		return data[index];
	}
	//修改数组中某一个元素
	public void set(int index,E e) {
		if(index<0||index>=size)
			throw new IllegalArgumentException("数组下标错误");
		data[index]=e;
	}
	//打印数组
	@Override
	public String toString() {
		StringBuilder res=new StringBuilder();
		res.append( String.format("数组的长度为=%d,数组的最大容量为=%d\n",size,data.length));
		res.append("[");
		 
		for(int i=0;i<size;i++)  {
			if(i!=size-1) {
			res.append(data[i]);
			res.append(", ");
			}
			 
		}
		res.append(data[size-1]+"]");
		return res.toString();
	}
	//查询是否包含某个元素
	public boolean contains(E e) {
		for(int i=0;i<size;i++)
		{
			if (data[i]==e)
				return true;
		}
		return false;
	}
	//搜索某个元素，并且返回其索引值
	public int find(E e) {
		for(int i=0;i<size;i++)	
			if (data[i]==e)
				return i;
		return -1;
	}
	//删除某个下标为index的元素
	public E remove(int index) {
		if(index<0||index>=size)
			throw new IllegalArgumentException("数组下标错误");
		E res=data[index];
		for(int i=index+1;i<size;i++)
			data[i-1]=data[i];
		size--;	
		data[size]=null;
		if(size==data.length/2)
			resize(data.length/2);
		return res;
	}
	//删除某个元素
	public void removeElement(E e) {
		 
			remove(find(e));	 
		
	}
	public E removeFirst() {
		return remove(0);
	}
	public E removeLast() {
		return remove(size-1);
	}

}
