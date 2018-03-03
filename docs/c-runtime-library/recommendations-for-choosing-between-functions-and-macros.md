---
title: "Doporučení k výběru mezi funkcemi a makry | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.functions
dev_langs:
- C++
helpviewer_keywords:
- functions [CRT], vs. macros
- macros, vs. functions
ms.assetid: 18a633d6-cf1c-470c-a649-fa7677473e2b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 810a4c2dbf5c80688dd739c48df0056ab394cafd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="recommendations-for-choosing-between-functions-and-macros"></a>Doporučení k výběru mezi funkcemi a makry
Většina rutiny běhové knihovny Microsoft kompilované nebo sestaví funkce, ale některé rutiny jsou implementované jako makra. Když soubor hlaviček deklaruje funkci a verze makro rutiny, definici makra má přednost před, protože se zobrazí vždy po deklaraci funkce. Při vyvolání rutiny, která je implementovaná jako funkce a makra, můžete vynutit kompilátoru na použití funkce verze dvěma způsoby:  
  
-   Uveďte název rutiny v závorkách.  
  
    ```  
    #include <ctype.h>  
    a = _toupper(a);    // Use macro version of toupper.  
    a = (_toupper)(a);  // Force compiler to use   
                        // function version of toupper.  
    ```  
  
-   "Nedefinované" definice makra s `#undef` – direktiva:  
  
    ```  
    #include <ctype.h>  
    #undef _toupper  
    ```  
  
 Pokud je třeba vybrat mezi funkce a implementace makro rutiny knihovny, zvažte následující kompromisy:  
  
-   **Rychlost a velikost** hlavní výhodou použití maker je rychlejší dobu provádění. Při předběžném zpracování, je rozšířena makra (nahrazené podle její definice) vloženého pokaždé, když se používá. Definice funkce dojde, je volána bez ohledu na to, jak často se pouze jednou. Makra může zvýšit velikost kód, ale nemají režie spojená s volání funkcí.  
  
-   **Vyhodnocení funkce** funkce vyhodnocuje adresu; makro neexistuje. Název makra proto nelze použít v kontextu, které vyžadují ukazatel. Můžou například deklarovat ukazatel na funkci, ale nikoli ukazatel na makra.  
  
-   **Kontrola typu** po deklarování funkce kompilátoru můžete zkontrolovat typy argumentů. Protože nelze deklarovat makra, kompilátor nelze zkontrolovat typy argumentů makro; i když ho můžete zkontrolovat počet argumentů předat makra.  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)