---
title: "Úložiště Thread Local | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- thread-local variables
- TLS (thread local storage)
- thread storage-class attribute
- thread-local storage
- storage, thread local storage
ms.assetid: a0f1b109-c953-4079-aa10-e47f5483173d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 46aaf6677a779ada2457814aecba5c84a59e1f1c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="thread-local-storage"></a>Úložiště Thread Local
**Konkrétní Microsoft**  
  
 Místní úložiště vláken (TLS) je mechanismus, pomocí kterého každé vlákno daného procesu přiděluje úložiště pro data specifické pro vlákno. U standardních aplikací s více vlákny jsou data sdílena mezi všemi vlákny daného procesu, kde místní úložiště vláken představuje mechanismus pro rozdělení dat pro vlákno. Úplné informace o vláken, najdete v části [vláken a procesů](http://msdn.microsoft.com/library/windows/desktop/ms684841) v [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 Jazyka Microsoft C obsahuje atribut Rozšířené třídy úložiště vláken, který se používá s __declspec – klíčové slovo deklarovat vlákna místní proměnné. Například následující kód deklaruje celé číslo vlákna místní proměnné a inicializuje s hodnotou:  
  
```  
__declspec( thread ) int tls_i = 1;  
```  
  
 Když jsou deklarace staticky vázané vláken v místních proměnných, musí být dodrženy těchto pokynů:  
  
-   Použití **__declspec(thread)** mohou ovlivňovat [zpoždění načítání](../build/reference/linker-support-for-delay-loaded-dlls.md) knihovny DLL importuje**.**  
  
-   Atribut vlákna můžete použít pouze na data deklarace a definice. Nelze zadat na funkce deklarace nebo definice. Například následující kód vygeneruje Chyba kompilátoru:  
  
    ```  
    #define Thread   __declspec( thread )  
    Thread void func();      /* Error */  
    ```  
  
-   Můžete zadat atribut vlákna pouze na datové položky s úložiště se statickými doba trvání. To zahrnuje globální data (statické a extern) a místní statických dat. Nelze deklarovat dat s atributem přístup z více vláken. Například následující kód generuje chyby kompilátoru:  
  
    ```  
    #define Thread   __declspec( thread )  
    void func1()  
    {  
        Thread int tls_i;            /* Error */  
    }  
  
    int func2( Thread int tls_i )    /* Error */  
    {  
       return tls_i;  
    }  
    ```  
  
-   Deklarace a definice místní data přístup z více vláken, bez ohledu na to, jestli deklarace a definice nastat ve stejném souboru nebo samostatné soubory musíte použít atribut vlákna. Například následující kód vygeneruje chybu:  
  
    ```  
    #define Thread   __declspec( thread )  
    extern int tls_i;     /* This generates an error, because the   */  
    int Thread tls_i;     /* declaration and the definition differ. */  
    ```  
  
-   Atribut vlákna nelze použít jako typ modifikátoru. Například následující kód vygeneruje Chyba kompilátoru:  
  
    ```  
    char *ch __declspec( thread );      /* Error */  
    ```  
  
-   Adresa vlákna místní proměnné není považována za konstantní a jakýkoli výraz zahrnující takové adresy se nepovažuje za konstantní výraz. To znamená, že nelze použít na adresu vlákna místní proměnné jako inicializátoru pro ukazatel. Například kompilátor flags následující kód jako chybu:  
  
    ```  
    #define Thread   __declspec( thread )  
    Thread int tls_i;  
    int *p = &tls_i;      /* Error */  
    ```  
  
-   C umožňuje inicializace proměnné s výrazem zahrnujícím odkaz sám na sebe, ale jenom pro nestatické objekty. Příklad:  
  
    ```  
    #define Thread   __declspec( thread )  
    Thread int tls_i = tls_i;             /* Error */  
    int j = j;                            /* Error */  
    Thread int tls_i = sizeof( tls_i )    /* Okay  */  
    ```  
  
     Všimněte si, že sizeof výraz, který obsahuje proměnnou během inicializace nepředstavuje odkaz sám na sebe a je povolen.  
  
-   Použití **__declspec(thread)** mohou ovlivňovat [zpoždění načítání](../build/reference/linker-support-for-delay-loaded-dlls.md) knihovny DLL importuje**.**  
  
 Další informace o používání atribut vlákna najdete v tématu [Multithreading témata](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Rozšířené atributy třídy úložiště jazyka C](../c-language/c-extended-storage-class-attributes.md)