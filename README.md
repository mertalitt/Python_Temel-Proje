# Python_Temel-Proje
{
 "cells": [
  {
   "cell_type": "markdown",
   "id": "d27aab53",
   "metadata": {},
   "source": [
    "# SORU 1 \n",
    "Bir listeyi düzleştiren (flatten) fonksiyon yazın. Elemanları birden çok katmanlı listelerden ([[3],2] gibi) oluşabileceği gibi, non-scalar verilerden de oluşabilir. Örnek olarak:\n",
    "\n",
    "input: [[1,'a',['cat'],2],[[[3]],'dog'],4,5]\n",
    "\n",
    "output: [1,'a','cat',2,3,'dog',4,5]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 1,
   "id": "8a4bd0fa",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "[1, 'a', 'cat', 2, 3, 'dog', 4, 5]\n"
     ]
    }
   ],
   "source": [
    "list1 = [[1,'a',['cat'],2],[[[3]],'dog'],4,5]\n",
    "flatten_list = []\n",
    "def flatten(l):\n",
    "    for sublist in l:\n",
    "        if type(sublist) == list:\n",
    "            flatten(sublist)\n",
    "        else:\n",
    "            flatten_list.append(sublist)\n",
    "    return flatten_list\n",
    "\n",
    "print(flatten(list1))"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "70026713",
   "metadata": {},
   "source": [
    "List Comprehension ile çözümü"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "id": "030fcb01",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "[1, 'a', 'cat', 2, 3, 'dog', 4, 5]\n"
     ]
    }
   ],
   "source": [
    "list1 = [[1,'a',['cat'],2],[[[3]],'dog'],4,5]\n",
    "flatten_list = []\n",
    "def flatten(l):\n",
    "    isFlatting = [flatten(sublist) if type(sublist) == list else flatten_list.append(sublist) for sublist in l]\n",
    "\n",
    "flatten(list1)\n",
    "print(flatten_list)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "faaac6b6",
   "metadata": {},
   "source": [
    "# SORU 2 \n",
    "Verilen listenin içindeki elemanları tersine döndüren bir fonksiyon yazın. Eğer listenin içindeki elemanlar da liste içeriyorsa onların elemanlarını da tersine döndürün. Örnek olarak:\n",
    "\n",
    "input: [[1, 2], [3, 4], [5, 6, 7]]\n",
    "\n",
    "output: [[[7, 6, 5], [4, 3], [2, 1]]"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "id": "55a0de2c",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "[[7, 6, 5], [4, 3], [2, 1]]\n"
     ]
    }
   ],
   "source": [
    "list1 = [[1, 2], [3, 4], [5, 6, 7]]  \n",
    "\n",
    "def reverse_list(l):\n",
    "    l.reverse()\n",
    "    for sublist in l:\n",
    "        if type(sublist) == list:\n",
    "            reverse_list(sublist)\n",
    "\n",
    "reverse_list(list1)\n",
    "print(list1)"
   ]
  },
  {
   "cell_type": "markdown",
   "id": "a3fd564d",
   "metadata": {},
   "source": [
    "List Comprehension ile çözümü"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "id": "c534dbe4",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "[[7, 6, 5], [4, 3], [2, 1]]\n"
     ]
    }
   ],
   "source": [
    "list1 = [[1, 2], [3, 4], [5, 6, 7]]  \n",
    "def reverse_list(l):\n",
    "    l.reverse()\n",
    "    reverse = [reverse_list(sublist) for sublist in l if type(sublist) == list]\n",
    "reverse_list(list1)\n",
    "print(list1)"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.8.8"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
