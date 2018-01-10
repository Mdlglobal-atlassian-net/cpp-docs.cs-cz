---
title: "Úložiště Thread Local (TLS) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 47e6be3645e03892d17e45256a5a003d982d973f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="thread-local-storage-tls"></a>Úložiště Thread Local (TLS)
Místní úložiště vláken (TLS) je metoda, pomocí kterého můžete přidělit každé vlákno daného procesu umístění pro uložení dat specifické pro vlákno. Dynamicky vázaná (runtime) specifické pro vlákno data jsou podporována prostřednictvím rozhraní API TLS ([TlsAlloc](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686801), [TlsGetValue](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686812), [TlsSetValue](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686818), a [TlsFree](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686804)). Další informace o tom, jak implementují lokální úložiště vláken v systému Windows najdete v tématu [lokální úložiště vláken (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686749\(v=vs.85\).aspx).  Win32 a kompilátor Visual C++ nyní podporují staticky vázané (čas načítání) dat pro vlákno kromě existující implementace rozhraní API.  
  
##  <a name="_core_compiler_implementation_for_tls"></a>Implementace kompilátoru TLS  
 **C ++ 11:** `thread_local` specifikátor třídy úložiště je doporučeným způsobem, jak určit úložiště thread-local pro objekty a třídy členy. Další informace najdete v tématu [třídy úložiště (C++)](../cpp/storage-classes-cpp.md).  
  
 Také poskytuje atribut specifické pro společnost Microsoft Visual C++ [vlákno](../cpp/thread.md), jako modifikátor třídy rozšířené úložiště. Použití `__declspec` – klíčové slovo deklarovat **vlákno** proměnné. Například následující kód deklaruje celé číslo vlákna místní proměnné a inicializuje s hodnotou:  
  
```  
__declspec( thread ) int tls_i = 1;  
```  
  
## <a name="rules-and-limitations"></a>Pravidla a omezení  
 Při deklarování staticky vázaného místní objekty vláken a proměnných, musí být dodrženy následující pokyny. Tyto pokyny platí i pro [vlákno](../cpp/thread.md)a ve většině případů také [thread_local](../cpp/storage-classes-cpp.md):  
  
-   `thread` Atribut lze použít pouze na třídu a data deklarace a definice. Nelze zadat na funkce deklarace nebo definice. Například následující kód vygeneruje Chyba kompilátoru:  
  
    ```  
  
    __declspec( thread )void func();     // This will generate an error.  
    ```  
  
-   `thread` Modifikátoru může zadat pouze u položek dat s `static` rozsah. To zahrnuje globální datové objekty (obojí `static` a `extern`), místní statické objekty a členy statických dat třídy jazyka C++. Automatické datové objekty nelze deklarovat s `thread` atribut. Následující kód generuje chyby kompilátoru:  
  
    ```  
  
    void func1()  
    {  
        __declspec( thread )int tls_i;            // This will generate an error.  
    }  
  
    int func2(__declspec( thread )int tls_i )    // This will generate an error.  
    {  
        return tls_i;  
    }  
    ```  
  
-   Deklarace a definice vlákna místní objektu musí být specifikovány `thread` atribut. Například následující kód vygeneruje chybu:  
  
    ```  
    #define Thread  __declspec( thread )  
    extern int tls_i;        // This will generate an error, since the  
    int __declspec( thread )tls_i;        // declaration and definition differ.  
    ```  
  
-   `thread` Nelze atribut použít jako typ modifikátoru. Například následující kód vygeneruje Chyba kompilátoru:  
  
    ```  
    char __declspec( thread ) *ch;        // Error  
    ```  
  
-   Protože deklarace C++ objekty, které používají `thread` atribut je povoleno, následující dva příklady jsou sémanticky ekvivalentní:  
  
    ```  
  
    __declspec( thread ) class B  
    {  
    // Code  
    } BObject;  // OK--BObject is declared thread local.  
  
    class B  
    {  
    // Code  
    };  
    __declspec( thread ) B BObject;  // OK--BObject is declared thread local.  
    ```  
  
-   Adresa vlákna místní objektu není považována za konstantní a jakýkoli výraz zahrnující takové adresy se nepovažuje za konstantní výraz. Důsledkem tohoto standardní C je nezakazuje používat adresu vlákna místní proměnné jako inicializátoru objektu nebo ukazatele. Například následující kód je označena jako chyba kompilátorem C:  
  
    ```  
  
    __declspec( thread )int tls_i;  
    int *p = &tls_i;       //This will generate an error in C.  
    ```  
  
     Toto omezení neplatí v jazyce C++. Protože C++ umožňuje dynamické inicializace všech objektů, bude možné inicializovat objekt pomocí výrazu, který používá adresu vlákna místní proměnné. To lze provést stejně jako konstrukce místní objekty vláken. Například následující kód dříve negeneruje chybu při kompilaci jako C++ zdrojového souboru. Všimněte si, že adresa vlákna místní proměnné je platný pouze dokud vlákno, ve kterém bylo provedeno adresování stále existuje.  
  
-   Standardní C umožňuje pro inicializaci objektu nebo proměnné s výrazem zahrnujícím odkaz sám na sebe, ale jenom pro nestatické objekty. I když C++ obecně umožňuje takové dynamické inicializace objektů s výrazem zahrnujícím odkaz sám na sebe, tento druh inicializace není povolena s místní objekty vláken. Příklad:  
  
    ```  
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++   
    int j = j;                               // OK in C++, error in C  
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++  
    ```  
  
     Všimněte si, že `sizeof` výraz, který obsahuje inicializovaný objekt nepředstavuje odkaz sám na sebe a je povolen v C a C++.  
  
     C++ nepovoluje takovou dynamickou inicializaci vlákno dat z důvodu možných budoucí vylepšení zařízení místní úložiště vláken.  
  
-   V operačních systémech Windows před [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)], `__declspec`(vlákno) má určitá omezení. Pokud se knihovna DLL deklaruje všechny dat nebo objekt jako `__declspec`(vlákno), může to způsobit chybu ochrany případě dynamicky načíst. Po načtení knihovny DLL s [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175), způsobuje selhání systému vždy, když kód odkazuje `__declspec`dat (vlákno). Vzhledem k tomu prostor globální proměnné vlákna v době běhu, velikost tohoto prostoru je založena na výpočtu požadavky na aplikace a požadavky na všechny knihovny DLL, které jsou staticky propojené. Při použití `LoadLibrary`, nelze rozšířit tento prostor pro lokální proměnné vláken deklarovat s `__declspec`(vlákno). Pomocí rozhraní API TLS, jako například [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801), v knihovně DLL přidělit TLS knihovnu DLL může být načtena s `LoadLibrary`.  
  
## <a name="see-also"></a>Viz také  
 [Multithreading s použitím jazyka C a prostředí Win32](../parallel/multithreading-with-c-and-win32.md)   
