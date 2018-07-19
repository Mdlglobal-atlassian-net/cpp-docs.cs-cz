---
title: omezení (C++ AMP) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- cpu_CPP
- amp_CPP
dev_langs:
- C++
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 175dcbbf94ff28b1f59804eb996254e29dfef243
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947636"
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)
Specifikátor omezení lze použít pro deklarace funkce i výrazu lambda. Vynucuje omezení kódu ve funkci a chování funkce v aplikacích používajících modul runtime C++ Accelerated Massive Parallelism (C++ AMP).  
  
> [!NOTE]
>  Informace o **omezit** – klíčové slovo, který je součástí **__declspec** atributy třídy úložiště, najdete v článku [omezit](../cpp/restrict.md).  
  
 **Omezit** klauzule mít následující podoby:  
  
|Klauzule|Popis|  
|------------|-----------------|  
|`restrict(cpu)`|Funkce může využívat celý jazyk C++. Funkci mohou volat pouze jiné funkce deklarované pomocí funkcí restrict(cpu).|  
|`restrict(amp)`|Funkce může používat pouze tu podmnožinu jazyka C++, kterou může knihovna C++ AMP urychlit.|  
|Sekvence specifikátorů `restrict(cpu)` a `restrict(amp)`.|Funkce musí dodržovat omezení specifikátoru `restrict(cpu)` i `restrict(amp)`. Funkci lze zavolat funkcemi deklarovanými pomocí specifikátorů `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` nebo `restrict(amp, cpu)`.<br /><br /> Tvar `restrict(A) restrict(B)` lze zapsat jako `restrict(A,B)`.|  
  
## <a name="remarks"></a>Poznámky  
 **Omezit** – klíčové slovo je kontextové klíčové slovo. Specifikátory omezení `cpu` a `amp` nejsou vyhrazenými slovy. Seznam specifikátorů nelze rozšířit. Funkce, která nemá **omezit** klauzule je stejný jako funkce, která má `restrict(cpu)` klauzuli.  
  
 Funkce obsahující klauzuli `restrict(amp)` má následující omezení:  
  
-   Funkce může volat pouze funkce obsahující klauzuli `restrict(amp)`.  
  
-   Funkci musí být možné vložit.  
  
-   Funkci lze deklarovat pouze **int**, **unsigned int**, **float**, a **double** proměnné a třídy a struktury, které obsahují pouze Tyto typy. **BOOL** také může, ale musí být 4 zarovnané bajtové použití ve složeném typu.  
  
-   Funkce lambda nedokážou zachytit ukazatele a hodnoty dle reference.  
  
-   Reference a ukazatele jedné dereference jsou podporovány pouze jako místní proměnné, argumenty funkce a návratové typy.  
  
-   Následující položky nejsou povoleny:  
  
    -   Rekurze.  
  
    -   Proměnné deklarované s [volatile](../cpp/volatile-cpp.md) – klíčové slovo.  
  
    -   Virtuální funkce.  
  
    -   Ukazatele na funkce.  
  
    -   Ukazatele na členské funkce.  
  
    -   Ukazatele ve strukturách.  
  
    -   Ukazatele na ukazatele.  
  
    -   **příkaz goto** příkazy.  
  
    -   Příkazy s popisky.  
  
    -   **Zkuste**, **catch**, nebo **throw** příkazy.  
  
    -   Globální proměnné.  
  
    -   Statické proměnné. Použití [tile_static – klíčové slovo](../cpp/tile-static-keyword.md) místo.  
  
    -   **přetypování dynamic_cast** přetypování.  
  
    -   **Typeid** operátor.  
  
    -   Deklarace asm.  
  
    -   Argumenty vararg.  
  
 Diskuzi o omezeních funkcí naleznete v tématu [omezení restrict(amp)](http://go.microsoft.com/fwlink/p/?LinkId=251089).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `restrict(amp)`klauzuli.  
  
```cpp 
  
void functionAmp() restrict(amp) {}   
void functionNonAmp() {}   
  
void callFunctions() restrict(amp)   
{   
    // int is allowed.  
    int x;  
    // long long int is not allowed in an amp-restricted function. This generates a compiler error.  
    // long long int y;   
  
    // Calling an amp-restricted function is allowed.  
    functionAmp();   
  
    // Calling a non-amp-restricted function is not allowed.  
    // functionNonAmp();   
  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)