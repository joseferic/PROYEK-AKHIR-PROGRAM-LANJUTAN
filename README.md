# PROYEK-AKHIR-PROGRAM-LANJUTAN

Proyek Akhir Program Lanjutan
Nama Proyek : Game Bingo 
Kelompok 12
Nama Anggota Kelompok :
1. Josef Eric (1806148725)
2. Fatur Rahman Stoffel (1806148675)

Game Bingo adalah game yang dimainkan bersama teman teman. 
Game ini mengharuskan kita mengacak angka dari 1 sampai 25 untuk masing-pemain.
Setelah diacak. 2 pemain tersebut melakukan suit. Bagi pemenang suit dapat giliran pertama dalam memilih angka untuk dilingkari.
angka yang dilingkari diprogram ini diberi angka 0.
secara bergantian pemain menyebutkan angka yang di lingkari.
pemenang dari game ini adalah mereka yang berhasil menyusun angka yang mereka acak secara horizontal / vertikal / diagonal sebanyak 5 kali untuk membuat 1 kata bingo.

-------------------------------------
struct node {
   int data;
   struct node *next;
};

kode diatas untuk membuat struct.
--------------------------------------
struct node *top1 = NULL;
struct node *current1 = NULL;

struct node *top2 = NULL;
struct node *current2= NULL;

kode diatas untuk membuat 2 jenis struct yang berbeda untuk tempat penyimpanan angka player.

-----------------------------------

void insert1(int data) {
   // Allocate memory for new node;
   struct node *link1 = (struct node*) malloc(sizeof(struct node));

	// Set value 
   link1->data = data;
   link1->next = NULL;

   // If top is empty, create new list
   if(top1==NULL) {
      top1 = link1;
      return;
   }

   current1 = top1;
   
   // move to the end of the list
   while(current1->next!=NULL)
      current1 = current1->next;
   
   // Insert link at the end of the list
   current1->next = link1; 
}

void insert2(int data) {
   // Allocate memory for new node;
   struct node *link2 = (struct node*) malloc(sizeof(struct node));

	// Set value 
   link2->data = data;
   link2->next = NULL;

   // If top is empty, create new list
   if(top2==NULL) {
      top2 = link2;
      return;
   }

   current2 = top2;
   
   // move to the end of the list
   while(current2->next!=NULL)
      current2 = current2->next;
   
   // Insert link at the end of the list
   current2->next = link2; 
}

kedua fungsi berguna untuk menyimpan angka dari 1 sampai 25 yang diacak para player.
-----------------------------------------------------------------------------------


void display1() {
   struct node *ptr1 = top1;
   int step=0;
 //  printf("\n[top] =>");
   //start from the beginning
   while(ptr1 != NULL) {
      printf("%d	",ptr1->data);
      ptr1 = ptr1->next;
      step+=1;
      if (step%5==0 && step>0)
	  {
	  	printf("\n");
	  }
   }

  // printf(" [null]\n");
}

void display2() {
   struct node *ptr2 = top2;
   int step=0;
 //  printf("\n[top] =>");
   //start from the beginning
   while(ptr2 != NULL) {
      printf("%d	",ptr2->data);
      ptr2 = ptr2->next;
      step+=1;
      if (step%5==0 && step>0)
	  {
	  	printf("\n");
	  }
   }
   
   fungsi diatas berguna untuk menampilkan angka angka yang di input oleh para player
   
  -------------------------------------------------------------------------------------
  
  void play1(int old) {
   int new=0;
   int pos = 0;
   
   if(top1==NULL) {
   	  system("cls");
      printf("\n\nAngka tidak ada\n\n");
      return;
   } 

   current1 = top1;
   while(current1->next!=NULL) {
      if(current1->data == old) {
         current1->data = new;
         //printf("\n%d ada diposisi U%d, diganti dengan %d\n", old, pos+1, new);
         return;
      }
      
      current1 = current1->next;
      pos++;
   }
   
   printf("%d tidak ada\n", old);
}

void play2(int old) {
   int new=0;
   int pos = 0;
   
   if(top2==NULL) {
   	  system("cls");
      printf("\n\nAngka tidak ada\n\n");
      return;
   } 

   current2 = top2;
   while(current2->next!=NULL) {
      if(current2->data == old) {
         current2->data = new;
         //printf("\n%d ada diposisi U%d, diganti dengan %d\n", old, pos+1, new);
         return;
      }
      
      current2 = current2->next;
      pos++;
   }
   
   printf("%d tidak ada\n", old);
}
 
 
 fungsi diatas berguna untuk menyimpan angka yang akan dilingkari. Karena keterbatasan kami. kami mengakalinya dengan menjadikan angka yang input bernilai 0.
 
 -----------------------------------------------------------------------------------------------------
  
  int cekBingo(int a, int b)
{
	system("cls");
	if (a==1)
	{
		printf("	B	");
	}
	else if (a==2)
	{
		printf("	B	");		
		printf("	I	");
	}
	else if (a==3)
	{
		printf("	B	");		
		printf("	I	");
		printf("	N	");		
	}
	else if (a==4)
	{
		printf("	B	");		
		printf("	I	");
		printf("	N	");		
		printf("	G	");
	}
	else if (a==5)
	{
		printf("	B	");		
		printf("	I	");
		printf("	N	");		
		printf("	G	");
		printf("	O	");
	}
	
	if (b==1)
	{
		printf("	B	");
	}
	else if (b==2)
	{
		printf("	B	");		
		printf("	I	");
	}
	else if (b==3)
	{
		printf("	B	");		
		printf("	I	");
		printf("	N	");		
	}
	else if (b==4)
	{
		printf("	B	");		
		printf("	I	");
		printf("	N	");		
		printf("	G	");
	}
	else if (b==5)
	{
		printf("	B	");		
		printf("	I	");
		printf("	N	");		
		printf("	G	");
		printf("	O	");
	}
	
	if (a==5 || b<5)
	{
		return 1;
	}
	else if (b==5 || a<5)
	{
		return 2;
	}
	else
	{
		return 0;
	}					
}

fungsi diatas berguna untuk menampilkan tulisan bingo. saat player berhasil setidaknya menyelesaikan 1 baris/kolom/diagonal miliknya

-------------------------------------------------------------------------------

int cekMenang(int *arr,int *arr2){
	int bingo1=0,bingo2=0;
//CEK PLAYER 1
//----BARIS-------
	if(arr[0]==0 && arr[1]==0 && arr[2]==0 && arr[3]==0 && arr[4]==0)
	{
		bingo1+=1;
	}
	return cekBingo(bingo1,bingo2);	
	if(arr[5]==0 && arr[6]==0 && arr[7]==0 && arr[8]==0 && arr[9]==0)
	{
		bingo1+=1;
	}
	return cekBingo(bingo1,bingo2);	
	if(arr[10]==0 && arr[11]==0 && arr[12]==0 && arr[13]==0 && arr[14]==0)
	{
		bingo1+=1;
	}
	return cekBingo(bingo1,bingo2);	
	if(arr[15]==0 && arr[16]==0 && arr[17]==0 && arr[18]==0 && arr[19]==0)
	{
		bingo1+=1;
	}
	return cekBingo(bingo1,bingo2);	
	if(arr[20]==0 && arr[21]==0 && arr[22]==0 && arr[23]==0 && arr[24]==0)
	{
		bingo1+=1;
	}
	return cekBingo(bingo1,bingo2);	
//----KOLOM-----
	if(arr[0]==0 && arr[5]==0 && arr[10]==0 && arr[15]==0 && arr[20]==0)
	{
		bingo1+=1;
	}
	return cekBingo(bingo1,bingo2);
	if(arr[1]==0 && arr[6]==0 && arr[11]==0 && arr[16]==0 && arr[21]==0)
	{
		bingo1+=1;
	}
	return cekBingo(bingo1,bingo2);	
	if(arr[2]==0 && arr[7]==0 && arr[12]==0 && arr[17]==0 && arr[22]==0)
	{
		bingo1+=1;
	}
	return cekBingo(bingo1,bingo2);	
	if(arr[3]==0 && arr[8]==0 && arr[13]==0 && arr[18]==0 && arr[23]==0)
	{
		bingo1+=1;
	}
	return cekBingo(bingo1,bingo2);	
	if(arr[4]==0 && arr[9]==0 && arr[14]==0 && arr[19]==0 && arr[24]==0)
	{
		bingo1+=1;
	}							
	return cekBingo(bingo1,bingo2);	
// -- DIAOGNAL ---
	if(arr[0]==0 && arr[6]==0 && arr[12]==0 && arr[18]==0 && arr[24]==0)
	{
		bingo1+=1;
	}
	return cekBingo(bingo1,bingo2);	
	if(arr[4]==0 && arr[8]==0 && arr[12]==0 && arr[16]==0 && arr[20]==0)
	{
		bingo1+=1;
	}	
	return cekBingo(bingo1,bingo2);
//CEK PLAYER 2
//----BARIS-------
	if(arr2[0]==0 && arr2[1]==0 && arr2[2]==0 && arr2[3]==0 && arr2[4]==0)
	{
		bingo2+=1;
	}
	cekBingo(bingo1,bingo2);	
	if(arr2[5]==0 && arr2[6]==0 && arr2[7]==0 && arr2[8]==0 && arr2[9]==0)
	{
		bingo2+=1;
	}
	cekBingo(bingo1,bingo2);	
	if(arr2[10]==0 && arr2[11]==0 && arr2[12]==0 && arr2[13]==0 && arr2[14]==0)
	{
		bingo2+=1;
	}
	cekBingo(bingo1,bingo2);	
	if(arr2[15]==0 && arr2[16]==0 && arr2[17]==0 && arr2[18]==0 && arr2[19]==0)
	{
		bingo2+=1;
	}
	cekBingo(bingo1,bingo2);	
	if(arr2[20]==0 && arr2[21]==0 && arr2[22]==0 && arr2[23]==0 && arr2[24]==0)
	{
		bingo2+=1;
	}
	cekBingo(bingo1,bingo2);	
//----KOLOM-----
	if(arr2[0]==0 && arr2[5]==0 && arr2[10]==0 && arr2[15]==0 && arr2[20]==0)
	{
		bingo2+=1;
	}
	cekBingo(bingo1,bingo2);	
	if(arr2[1]==0 && arr2[6]==0 && arr2[11]==0 && arr2[16]==0 && arr2[21]==0)
	{
		bingo2+=1;
	}
	cekBingo(bingo1,bingo2);	
	if(arr2[2]==0 && arr2[7]==0 && arr2[12]==0 && arr2[17]==0 && arr2[22]==0)
	{
		bingo2+=1;
	}
	cekBingo(bingo1,bingo2);	
	if(arr2[3]==0 && arr2[8]==0 && arr2[13]==0 && arr2[18]==0 && arr2[23]==0)
	{
		bingo2+=1;
	cekBingo(bingo1,bingo2);		
	}
	if(arr2[4]==0 && arr2[9]==0 && arr2[14]==0 && arr2[19]==0 && arr2[24]==0)
	{
		bingo2+=1;
	}							
	cekBingo(bingo1,bingo2);	
// -- DIAOGNAL ---
	if(arr2[0]==0 && arr2[6]==0 && arr2[12]==0 && arr2[18]==0 && arr2[24]==0)
	{
		bingo2+=1;
	}
	cekBingo(bingo1,bingo2);	
	if(arr2[4]==0 && arr2[8]==0 && arr2[12]==0 && arr2[16]==0 && arr2[20]==0)
	{
		bingo2+=1;
	}
	cekBingo(bingo1,bingo2);		
}

fungsi diatas ini berguna untuk mengecek apakah sudah 1 baris / 1 kolom / 1 diagonal telah diselesaikan.
-------------------------------------------------------------------------------------------------------

int main() {
  int arr[25],arr2[25], i, j, k,l, size=25,size2=25,in,step=0,size1;
  int MenangSuit=0,menang=0,input;
   
//------------ PLAYER 1 ------------------   
   for (i = 0; i < size; i++)
   {
   for(l=0; l<25; l++)
   {
   		if(l>0 && l%5==0)
		{
			printf("\n");   
		}
		if(arr[l]%26!=0 && arr[l]>0)
		{
	//	printf("U%d	",l+1);
   		printf("%d	",arr[l]);
	   	}
   		else
		   {
		   	printf("U%d	",l+1);
		   }
   }
	printf("\n\nInput U%d = ",i+1);scanf("%d", &in);
	while(in<=0 || in>25)
	  {
	  	system("cls");
   		for(l=0; l<25; l++)
   		{
   		if(l>0 && l%5==0)
		{
			printf("\n");   
		}
		if(arr[l]%26!=0 && arr[l]>0)
		{
	//	printf("U%d	",l+1);
   		printf("%d	",arr[l]);
	   	}
   		else
		   {
		   	printf("U%d	",l+1);
		   }
   		}	  	
		printf("\n\nInput hanya 1 sampai 25\n\nInput U%d = ",i+1);scanf("%d", &in);
					  	
//		printf("\n\nInput hanya 1 sampai 25\n\n");	 
	  }
		arr[i]=in;
		system("cls");
	//	step+=1;
	}
//		printf("Step =	%d",step);	
   //printf("\nList of Unique Numbers:");
   for (i = 0; i < size; i++) {
      for (j = i + 1; j < size;) {
         if (arr[j] == arr[i]) {
            for (k = j; k < size; k++) {
               arr[k] = arr[k + 1];
            }
            size--;
         } else
            j++;
      }
   }
   size1= size;
  // printf("\n\nSize = %d\n\n",size1);
 /*  for (i = 0; i < size; i++) {
      printf("%d ", arr[i]);
   }
   */
   if (size1<25)
   {
   for (size1; size1 < 25; size1++)
    {
	system("cls");
   		for(l=0; l<25; l++)
   		{
   		if(l>0 && l%5==0)
		{
			printf("\n");   
		}
		if(arr[l]%26!=0 && arr[l]>0)
		{
	//	printf("U%d	",l+1);
   		printf("%d	",arr[l]);
	   	}
   		else
		   {
		   	printf("U%d	",l+1);
		   }
   		}		    	
	printf("\n\nInput U%d = ",size1+1);scanf("%d", &in);
	while(in<0 || in>25 )
	  {
	  	system("cls");
   		for(l=0; l<25; l++)
   		{
   		if(l>0 && l%5==0)
		{
			printf("\n");   
		}
		if(arr[l]%26!=0 && arr[l]>0)
		{
	//	printf("U%d	",l+1);
   		printf("%d	",arr[l]);
	   	}
   		else
		   {
		   	printf("U%d	",l+1);
		   }
   		}		
		printf("\n\nInput hanya 1 sampai 25\n\nInput U%d = ",size1+1); scanf("%d", &in);
//		printf("\n\nInput hanya 1 sampai 25\n\n");
	//printf("Input U%d = ",size1+1); scanf("%d", &in);			  	
	  }
		arr[size1]=in;
		system("cls");
//		step+=1;
	}   	
   }
   else
   {
   for(l=0; l<25; l++)
   {
   		if(l>0 && l%5==0)
		{
			printf("\n");   
		}
		if(arr[l]%26!=0 && arr[l]>0)
		{
	//	printf("U%d	",l+1);
   		printf("%d	",arr[l]);
	   	}
   		else
		   {
		   	printf("U%d	",l+1);
		   }
   }
   }
   for (i=0; i<25; i++)
   {
   		insert1(arr[i]);
   }	
	printf("\n\n----------------------");
	system("cls");
//---------PLAYER 2------------------
   
   size=25;
   for (i = 0; i < size; i++)
   {
   for(l=0; l<25; l++)
   {
   		if(l>0 && l%5==0)
		{
			printf("\n");   
		}
		if((arr2[l]%26!=0 && arr2[l]>0))
		{
	//	printf("U%d	",l+1);
   		printf("%d	",arr2[l]);
	   	}
   		else
		   {
		   	printf("U%d	",l+1);
		   }
   }
	printf("\n\nInput U%d = ",i+1);scanf("%d", &in);
	while(in<0 || in>25)
	  {
	  	system("cls");
   		for(l=0; l<25; l++)
   		{
   		if(l>0 && l%5==0)
		{
			printf("\n");   
		}
		if(arr2[l]%26!=0 && arr2[l]>0)
		{
	//	printf("U%d	",l+1);
   		printf("%d	",arr2[l]);
	   	}
   		else
		   {
		   	printf("U%d	",l+1);
		   }
   		}
		printf("\n\nInput hanya 1 sampai 25\n\nInput U%d = ",i+1);scanf("%d", &in);			  	
//		printf("\n\nInput hanya 1 sampai 25\n\n");	  
	  }
		arr2[i]=in;
		system("cls");
	//	step+=1;
	}
//		printf("Step =	%d",step);	
   //printf("\nList of Unique Numbers:");
   for (i = 0; i < size; i++) {
      for (j = i + 1; j < size;) {
         if (arr[j] == arr[i]) {
            for (k = j; k < size; k++) {
               arr[k] = arr[k + 1];
            }
            size--;
         } else
            j++;
      }
   }
   size2= size;
  // printf("\n\nSize = %d\n\n",size1);
 /*  for (i = 0; i < size; i++) {
      printf("%d ", arr[i]);
   }
   */
   if (size2<25)
   {
   for (size2; size2 < 25; size2++)
    {
   for (i = 0; i < size; i++)
   {
   for(l=0; l<25; l++)
   {
   		if(l>0 && l%5==0)
		{
			printf("\n");   
		}
		if(arr2[l]%26!=0 && arr2[l]>0)
		{
	//	printf("U%d	",l+1);
   		printf("%d	",arr2[l]);
	   	}
   		else
		   {
		   	printf("U%d	",l+1);
		   }
   }
	printf("\n\nInput U%d = ",i+1);scanf("%d", &in);
	while(in<0 || in>25)
	  {
	  	system("cls");
   		for(l=0; l<25; l++)
   		{
   		if(l>0 && l%5==0)
		{
			printf("\n");   
		}
		if(arr2[l]%26!=0 && arr2[l]>0)
		{
	//	printf("U%d	",l+1);
   		printf("%d	",arr2[l]);
	   	}
   		else
		   {
		   	printf("U%d	",l+1);
		   }
   		}
		printf("\n\nInput hanya 1 sampai 25\n\nInput U%d = ",i+1);scanf("%d", &in);		  	
	//	printf("\n\nInput hanya 1 sampai 25\n\n");	
	  }
		arr[size2]=in;
		system("cls");
//		step+=1;
	}   	
   }
	}
   else
   {
   for(l=0; l<25; l++)
   {
   		if(l>0 && l%5==0)
		{
			printf("\n");   
		}
		if(arr2[l]%26!=0 && arr2[l]>0)
		{
	//	printf("U%d	",l+1);
   		printf("%d	",arr2[l]);
	   	}
   		else
		   {
		   	printf("U%d	",l+1);
		   }
   }
   }
   for (i=0; i<25; i++)
   {
   		insert2(arr2[i]);
   }	   
   
   printf("\n\n\n\n");
   system("cls");
   display2();   
   printf("\n\n----------------------");
   system("cls");   

   display1();
   printf("\n\n\n\n");
   display2();
   sleep(2);
   system("cls");
   MenangSuit=1;

   if (MenangSuit==1)
   {
   		while(menang==0)
		   {
		   		display1();
		   		printf("\n\nPlayer 1\n\nMasukan Angka yang akan dilingkari (diberi nilai 0)	  =	"); scanf("%d",&input);
		   		sleep(2);
				system("cls");
		   		play1(input); play2(input);   		   		
		   		menang = cekMenang(arr,arr2);
		   		sleep(2);
				system("cls");
				display2();
		   		printf("\n\nPlayer 2\n\nMasukan Angka yang akan dilingkari (diberi nilai 0)	  =	"); scanf("%d",&input);
		   		sleep(2);
				system("cls");
		   		play1(input); play2(input); 		   		
				menang = cekMenang(arr,arr2);
		   }
   }
   
   else if (MenangSuit==2)
   {
   		while(menang==0)
		   {
		   		display2();
		   		printf("\n\nPlayer 2\n\nMasukan Angka yang akan dilingkari (diberi nilai 0)	  =	"); scanf("%d",&input);
		   		sleep(2);
				system("cls");
		   		play1(input); play2(input); 
				display1();
				menang = cekMenang(arr,arr2);
		   		printf("\n\nPlayer 1\n\nMasukan Angka yang akan dilingkari (diberi nilai 0)	  =	"); scanf("%d",&input);
		   		sleep(2);
				system("cls");
		   		play1(input); play2(input); 		   		
				menang = cekMenang(arr,arr2);
		   }   	
   }

 
   return 0;
}

fungsi ini adalah fungsi main dari proyek ini
------------------------------------------------
PENJELASAN FUNGSI MAIN
------------------------------------------------
  int arr[25],arr2[25], i, j, k,l, size=25,size2=25,in,step=0,size1;
  int MenangSuit=0,menang=0,input;
  
  arr[25], arr2[25] adalah tempat penyimpanan dari angka yang diinput. selain menggunakan linked list kami juga menggunakan array
  i,j,k,l variabel untuk looping
  size1,size2,size merupakan variabel yang dipakai untuk ukuran dari array saat dijalankan.
  MenangSuit, merupakan variabel yang dipakai untuk masuk loop dari game sampai bernilai 1 atau 2. 1 berarti player 1 menang suit. begitu    sebaliknya
  menang merupakan variabel yang dipakai untuk masuk loop dari game sampai bernilai 1 atau 2. 1 berarti player 1 menang game. begitu    sebaliknya
  input variabel yang dipakai untuk meminta input dari user berupa angka yang akan dilingkari ( dalam proyek ini diganti jadi angka 0 )
  ------------------------------------------
     for (i = 0; i < size; i++)
   {
   for(l=0; l<25; l++)
   {
   		if(l>0 && l%5==0)
		{
			printf("\n");   
		}
		if(arr[l]%26!=0 && arr[l]>0)
		{
	//	printf("U%d	",l+1);
   		printf("%d	",arr[l]);
	   	}
   		else
		   {
		   	printf("U%d	",l+1);
		   }
   }
   potongan kode diatas berfungsi untuk menampilkan skema dan angka yang telah diinput oleh para player.
   -------------------------------------------------
   
   	printf("\n\nInput U%d = ",i+1);scanf("%d", &in);
	while(in<=0 || in>25)
	  {
	  	system("cls");
   		for(l=0; l<25; l++)
   		{
   		if(l>0 && l%5==0)
		{
			printf("\n");   
		}
		if(arr[l]%26!=0 && arr[l]>0)
		{
	//	printf("U%d	",l+1);
   		printf("%d	",arr[l]);
	   	}
   		else
		   {
		   	printf("U%d	",l+1);
		   }
   		}	  	
		printf("\n\nInput hanya 1 sampai 25\n\nInput U%d = ",i+1);scanf("%d", &in);
					  	
//		printf("\n\nInput hanya 1 sampai 25\n\n");	 
	  }
		arr[i]=in;
		system("cls");
	//	step+=1;
	}
//		printf("Step =	%d",step);	
   //printf("\nList of Unique Numbers:");
   for (i = 0; i < size; i++) {
      for (j = i + 1; j < size;) {
         if (arr[j] == arr[i]) {
            for (k = j; k < size; k++) {
               arr[k] = arr[k + 1];
            }
            size--;
         } else
            j++;
      }
   }
   size1= size;
  // printf("\n\nSize = %d\n\n",size1);
 /*  for (i = 0; i < size; i++) {
      printf("%d ", arr[i]);
   }
   */
  
  potongan kode diatas berguna untuk menampilkan kembali skema saat player memberikan input berupa
  1. character
  2. angka <0 dan angka > 25
  3. angka berulang
  ---------------------------------------------------------------------------------------------
  if (size1<25)
   {
   for (size1; size1 < 25; size1++)
    {
	system("cls");
   		for(l=0; l<25; l++)
   		{
   		if(l>0 && l%5==0)
		{
			printf("\n");   
		}
		if(arr[l]%26!=0 && arr[l]>0)
		{
	//	printf("U%d	",l+1);
   		printf("%d	",arr[l]);
	   	}
   		else
		   {
		   	printf("U%d	",l+1);
		   }
   		}		    	
	printf("\n\nInput U%d = ",size1+1);scanf("%d", &in);
	while(in<0 || in>25 )
	  {
	  	system("cls");
   		for(l=0; l<25; l++)
   		{
   		if(l>0 && l%5==0)
		{
			printf("\n");   
		}
		if(arr[l]%26!=0 && arr[l]>0)
		{
	//	printf("U%d	",l+1);
   		printf("%d	",arr[l]);
	   	}
   		else
		   {
		   	printf("U%d	",l+1);
		   }
   		}		
		printf("\n\nInput hanya 1 sampai 25\n\nInput U%d = ",size1+1); scanf("%d", &in);
//		printf("\n\nInput hanya 1 sampai 25\n\n");
	//printf("Input U%d = ",size1+1); scanf("%d", &in);			  	
	  }
		arr[size1]=in;
		system("cls");
//		step+=1;
	}   	
   }
   else
   {
   for(l=0; l<25; l++)
   {
   		if(l>0 && l%5==0)
		{
			printf("\n");   
		}
		if(arr[l]%26!=0 && arr[l]>0)
		{
	//	printf("U%d	",l+1);
   		printf("%d	",arr[l]);
	   	}
   		else
		   {
		   	printf("U%d	",l+1);
		   }
   }
   }
   
   kode diatas beguna untuk menyeleksi apakah angka ada yang berulang dan angka kurang dari 25 buah.
   -------------------------------------------------------------------------------------------------
   
      for (i=0; i<25; i++)
   {
   		insert1(arr[i]);
   }	
	printf("\n\n----------------------");
	system("cls");
 
 kode diatas berguna untuk menyimpan data yang ada diarray sehingga di input kedalam fungsi insert. secara 1 per 1.
 ----------------------------------------------------------------------
 
 proyek ini menggunkan linked list
 proyek ini menggunakan dynamic storage
 
  
  
  
  
