---
title: omezení (C++ AMP) | Microsoft Docs
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
ms.openlocfilehash: abe3bd4f737cfb26a326a1f0d83b731c36e6c7bf
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)
Specifikátor omezení lze použít pro deklarace funkce i výrazu lambda. Vynucuje omezení kódu ve funkci a chování funkce v aplikacích používajících modul runtime C++ Accelerated Massive Parallelism (C++ AMP).  
  
> [!NOTE]
>  Informace o `restrict` – klíčové slovo, který je součástí `__declspec` atributy třídy úložiště, najdete v části [omezit](../cpp/restrict.md).  
  
 Klauzule `restrict` může mít následující podoby:  
  
|Klauzule|Popis|  
|------------|-----------------|  
|`restrict(cpu)`|Funkce může využívat celý jazyk C++. Funkci mohou volat pouze jiné funkce deklarované pomocí funkcí restrict(cpu).|  
|`restrict(amp)`|Funkce může používat pouze tu podmnožinu jazyka C++, kterou může knihovna C++ AMP urychlit.|  
|Sekvence specifikátorů `restrict(cpu)` a `restrict(amp)`.|Funkce musí dodržovat omezení specifikátoru `restrict(cpu)` i `restrict(amp)`. Funkci lze zavolat funkcemi deklarovanými pomocí specifikátorů `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` nebo `restrict(amp, cpu)`.<br /><br /> Tvar `restrict(A) restrict(B)` lze zapsat jako `restrict(A,B)`.|  
  
## <a name="remarks"></a>Poznámky  
 Klíčové slovo `restrict` je kontextovým klíčovým slovem. Specifikátory omezení `cpu` a `amp` nejsou vyhrazenými slovy. Seznam specifikátorů nelze rozšířit. Funkce neobsahující klauzuli `restrict` je shodná s funkcí obsahující klauzuli `restrict(cpu)`.  
  
 Funkce obsahující klauzuli `restrict(amp)` má následující omezení:  
  
-   Funkce může volat pouze funkce obsahující klauzuli `restrict(amp)`.  
  
-   Funkci musí být možné vložit.  
  
-   Funkce může deklarovat pouze proměnné typu `int`, `unsigned int`, `float` a `double` a třídy a struktury obsahující pouze tyto typy. Typ `bool` je povolen také, pro použití ve složeném typu však musí být zarovnán na 4 bajty.  
  
-   Funkce lambda nedokážou zachytit ukazatele a hodnoty dle reference.  
  
-   Reference a ukazatele jedné dereference jsou podporovány pouze jako místní proměnné, argumenty funkce a návratové typy.  
  
-   Následující položky nejsou povoleny:  
  
    -   Rekurze.  
  
    -   Proměnné deklarovat s [volatile](../cpp/volatile-cpp.md) – klíčové slovo.  
  
    -   Virtuální funkce.  
  
    -   Ukazatele na funkce.  
  
    -   Ukazatele na členské funkce.  
  
    -   Ukazatele ve strukturách.  
  
    -   Ukazatele na ukazatele.  
  
    -   Příkazy `goto`.  
  
    -   Příkazy s popisky.  
  
    -   Příkazy `try`, `catch` nebo `throw`.  
  
    -   Globální proměnné.  
  
    -   Statické proměnné. Použití [tile_static – klíčové slovo](../cpp/tile-static-keyword.md) místo.  
  
    -   Přetypování `dynamic_cast`.  
  
    -   Operátor `typeid`.  
  
    -   Deklarace asm.  
  
    -   Argumenty vararg.  
  
 Informace funkce omezení, naleznete v [restrict(amp) omezení](http://go.microsoft.com/fwlink/p/?LinkId=251089).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `restrict(amp)`klauzule.  
  
```  
  
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