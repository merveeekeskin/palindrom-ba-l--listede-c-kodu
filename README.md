# palindrom-ba-l--listede-c-kodu
palindrom bağlı listenin amacı:

Palindrom bağlı listenin amacı, palindromik verileri depolamak ve bu verileri kolayca erişilebilir hale getirmektir.
Palindrom bağlı listenin birçok farklı kullanımı vardır, 
örneğin bir kelime veya sayının palindrom olup olmadığını kontrol etmek, 
belirli bir palindromik kelimenin sıklığını bulmak veya palindromik bir kelime grubunun en uzun palindromik alt dizisini bulmak gibi işlemler için kullanılabilir.


palindrom bağlı liste ne için kullanılır:

Palindrom bağlı listeleri, karakter dizilerinin her iki uçtan eşleştiğinde bir palindrom oluşturup oluşturmadığını kontrol etmek için kullanabilirsiniz.
Bu işlem, özellikle otomatik düzeltme özelliklerinin uygulandığı kelime işlemcileri, yazılım geliştirme araçları ve veri analiz araçları gibi birçok alanda kullanılır.
 bir metin belgesindeki palindromik kelimeleri veya cümleleri bulmak için kullanılabilirler.
 Ayrıca, bu tür bağlı listeler, yineleyici ve rekürsif algoritmaların tasarımında kullanılabilirler. 
 Palindrom bağlı listeleri kullanarak algoritma soruları da yaygın olarak sorulmaktadır.
 
 
 palindrom bağlı listenin çalışma biçimi
 Bir palindrom bağlı listenin çalışma şekli şu şekildedir:

Liste, başlangıçta boş bir düğümle başlar.
Elemanlar tek tek bağlı liste üzerine eklenir.
Her eklemede, yeni bir düğüm oluşturulur ve bağlı listenin sonuna eklenir.
Elemanların palindrom oluşturacak şekilde eklenmesi için, elemanlar önce baştan sona doğru, sonra da sondan başa doğru eklenir. 
Bu nedenle, önce ilk eleman bağlı listenin sonuna eklenir, ardından son eleman bağlı listenin başına eklenir ve bu şekilde devam edilir.
Liste tamamlandığında, bağlı listenin başından ve sonundan başlayarak okunarak palindrom olup olmadığı kontrol edilir.
Eğer liste bir palindrom ise, true değeri döndürülür. Aksi takdirde, false değeri döndürülür.

polindrom bağlı listenin c kodu
(açıklama:Tek bağlı bir listenin head bilgisi verildiğinde verildiğinde,bu liste palindrom ise true döndürür.)



#include <stdio.h>

#include <stdlib.h>

#include <stdbool.h>

// Bağlı listenin düğüm yapısı 


struct Node {


    char data;
    struct Node* next;};

// Yeni bir düğüm oluşturma fonksiyonu


struct Node* newNode(char data) {


    struct Node* node = (struct Node*) malloc(sizeof(struct Node));
    node->data = data;
    node->next = NULL;
    return node;
}

// Palindrom bağlı listenin kontrol fonksiyonu 


bool isPalindrome(struct Node* head) {


    struct Node* slow = head;
    struct Node* fast = head;
    struct Node* prev = NULL;
    struct Node* curr = head;
    struct Node* next = NULL;
    bool isPalin = true;

    //Listenin orta noktasını bulma 
    while (fast != NULL && fast->next != NULL) {
        fast = fast->next->next;
        prev = slow;
        slow = slow->next;
    }

    // Listenin ortasından sonuna kadar olan düğümlerin ters çevrilmesi 
    prev->next = NULL;
    while (slow != NULL) {
        next = slow->next;
        slow->next = curr;
        curr = slow;
        slow = next;
    }

    //İki yarıyı karşılaştırma 
    while (curr != NULL) {
        if (head->data != curr->data) {
            isPalin = false;
            break;
        }
        head = head->next;
        curr = curr->next;
    }

    //Listenin eski haline getirilmesi 
    slow = NULL;
    while (prev != NULL) {
        next = prev->next;
        prev->next = slow;
        slow = prev;
        prev = next;
    }
    head->next = slow;

    return isPalin;
    
    
}


// Palindrom bağlı liste oluşturma ve test etme 


int main() {


    struct Node* head = newNode('r');
    
    
    head->next = newNode('a');
    
    
    head->next->next = newNode('d');
    
    
    head->next->next->next = newNode('a');
    
    
    head->next->next->next->next = newNode('r');
    
    

    if (isPalindrome(head))
    
    
        printf("Bu liste bir palindromdur.\n");
        
        
    else
    
    
        printf("Bu liste bir palindrom degildir.\n");
        
        

    return 0;
}










