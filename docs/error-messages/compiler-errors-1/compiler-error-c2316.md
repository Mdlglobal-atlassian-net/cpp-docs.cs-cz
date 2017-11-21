---
title: "C2316 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2316
dev_langs: C++
helpviewer_keywords: C2316
ms.assetid: 9ad08eb5-060b-4eb0-8d66-0dc134f7bf67
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8fa8426f89d0d61ff32facb3ab0b15ac5b770e94
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2316"></a>C2316 chyby kompilátoru

> '*výjimka*': nemůže být zachycena, jako jsou nedostupné destruktor nebo kopírovací konstruktor  
  
Byla výjimka zachycena hodnotou nebo odkazem ale konstruktor copy nebo operátor přiřazení byly nedostupné.  
  
Tento kód byl přijat ve verzích Visual C++ před Visual Studio 2003, ale teď obsahuje chybu.  
  
Tato chyba, platí pro příkazy chybný catch – zpracování výjimek MFC odvozené od provedeny změny shoda v sadě Visual Studio 2015 `CException`. Protože `CException` má zděděné privátní kopie konstruktoru, třída a odvozené jsou bez kopírovatelná a nelze předat podle hodnoty, to také znamená nemůže být zachycena hodnotou. Catch – příkazy, které zachytila MFC – výjimky hodnota dříve vedla k nezachycená výjimky za běhu, ale teď kompilátor správně identifikuje této situaci a sestavy chyb C2316. Chcete-li tento problém vyřešit, doporučujeme že použít MFC TRY/CATCH – makra místo psát vlastní obslužné rutiny výjimek, ale pokud to není vhodné pro váš kód, zachycení výjimek MFC odkazem místo.   
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2316:  
  
```  
// C2316.cpp  
// compile with: /EHsc  
#include <stdio.h>  
  
extern "C" int printf_s(const char*, ...);  
  
struct B   
{  
public:  
    B() {}  
    // Delete the following line to resolve.  
private:  
    // copy constructor  
    B(const B&)   
    {  
    }  
};  
  
void f(const B&)   
{  
}  
  
int main()   
{  
    try   
    {  
        B aB;  
        f(aB);  
    }  
    catch (B b) {   // C2316  
        printf_s("Caught an exception!\n");     
    }  
}  
```