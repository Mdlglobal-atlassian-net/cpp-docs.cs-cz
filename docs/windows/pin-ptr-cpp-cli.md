---
title: pin_ptr (C + +/ CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- pin_ptr_cpp
- stdcli::language::pin_ptr
- pin_ptr
dev_langs:
- C++
helpviewer_keywords:
- pinning pointers
- pin_ptr keyword [C++]
ms.assetid: 6c2e6c73-4ec2-4dce-8e1f-ccf3a9f9d0aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: afc99a352e0bde7918cab460293ff23061377551
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="pinptr-ccli"></a>pin_ptr (C++/CLI)
Deklaruje *Připnutí ukazatelů*, který se používá jenom s modul common language runtime.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 (Používají se žádné poznámky pro tuto funkci jazyka, které platí pro všechny moduly runtime.)  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 (Tento jazyk funkce není podporována v prostředí Windows Runtime).  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime)  
 A *Připnutí ukazatelů* vnitřní ukazatel, která zabraňuje objekt ukazuje z přesunutí v haldě uvolňování paměti. To znamená není změnit hodnotu Připnutí ukazatel modul common language runtime. To je potřeba, při předání adresu spravované třídy nespravované funkce tak, aby adresu nezmění neočekávaně během řešení volání nespravovaných funkcí.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;  
```  
  
### <a name="parameters"></a>Parametry  
 *cv_qualifier*  
 `const` nebo `volatile` kvalifikátory. Ve výchozím nastavení, je připnutý ukazatel `volatile`. Je ale nejde o chybu deklarovat Připnutí ukazatel redundantní `volatile`.  
  
 *Typ*  
 Typ `initializer`.  
  
 *var*  
 Název `pin_ptr` proměnné.  
  
 *Inicializátor*  
 Člen odkaz, element spravovaného pole nebo jakýkoliv jiný objekt, který lze přiřadit nativní ukazatel.  
  
### <a name="remarks"></a>Poznámky  
 A `pin_ptr` představuje nadmnožinou funkce nativní ukazatel. Proto všechny položky, které lze přiřadit k nativní ukazatel můžete taky přiřadit ke `pin_ptr`. Vnitřní ukazatel oprávněn provádět stejnou sadu operací, jako nativními ukazateli, včetně porovnání a aritmetika ukazatele.  
  
 Na objekt nebo dílčí objekt spravované třídy, můžete připnuli, v takovém případě modul CLR nebude ho přesunout během uvolňování paměti. Hlavní použití tohoto objektu je předat ukazatel spravovaných dat jako skutečný parametr volání nespravovaných funkcí. Během cyklu kolekce modul runtime bude kontrolovat metadata vytvořené pro Připnutí ukazatelů a nepřesune položku, kterou se odkazuje.  
  
 Připnutí objekt také PIN kódy jeho hodnota pole; To znamená pole primitivních nebo hodnota typu. Ale deklarovaná sledovací popisovač pole (`%`) nejsou připnutý.  
  
 Připnutí dílčí objekt definovaný v spravovaného objektu má za následek Připnutí celý objekt.  
  
 Pokud tak, aby odkazoval na novou hodnotu opětovně přiřazován Připnutí ukazatelů, předchozí instanci ukazuje je nelze nadále považovat za připnutý.  
  
 Objekt je připnutá pouze při `pin_ptr` body k němu. Objekt je již připojena při jeho Připnutí ukazatelů ocitne mimo rozsah, nebo je nastaven na [nullptr](../windows/nullptr-cpp-component-extensions.md). Po `pin_ptr` přejde mimo obor, objekt, který byl připnutý lze přesunout v haldě modulem garbage collector. Všechny nativní ukazatele, které stále odkazovat objekt se nebude aktualizovat a zrušte odkazující na jeden z nich by mohly znamenat vyšší neopravitelné výjimky.  
  
 Pokud žádné přídavných ukazatelů bodu k objektu (všechny přídavných ukazatelů byla mimo rozsah, přejděte na další objekty byly přiřazeny nebo byly přiřazené [nullptr](../windows/nullptr-cpp-component-extensions.md)), objekt záruku, že se tak, aby byla připojená.  
  
 Připnutí ukazatel může ukazovat na popisovač odkaz na typ hodnoty nebo zabalený typ popisovače, členem spravovaný typ, nebo element spravovaného pole. Nemůže odkazovat na odkazového typu.  
  
 S ohledem na adresu `pin_ptr` , odkazuje na objekt nativní způsobí, že nedefinované chování.  
  
 Přídavných ukazatelů lze deklarovat pouze jako místní proměnné nestatické v zásobníku.  
  
 Přídavných ukazatelů nelze použít jako:  
  
-   funkční parametry  
  
-   Návratový typ funkce  
  
-   člen třídy  
  
-   cílový typ přetypování.  
  
 `pin_ptr` Probíhá `cli` oboru názvů. Další informace najdete v tématu [Platform, default a rozhraní příkazového řádku obory názvů](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md).  
  
 Další informace o vnitřních ukazatelů najdete v tématu [interior_ptr (C + +/ CLI)](../windows/interior-ptr-cpp-cli.md).  
  
 Další informace o přídavné ukazatele najdete v tématu [postup: Pin ukazatelů a polí](../windows/how-to-pin-pointers-and-arrays.md) a [postupy: deklarace Připnutí ukazatelů a typů hodnot](../windows/how-to-declare-pinning-pointers-and-value-types.md).  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad používá `pin_ptr` omezit pozice první prvek pole.  
  
```  
// pin_ptr_1.cpp  
// compile with: /clr   
using namespace System;  
#define SIZE 10  
  
#pragma unmanaged  
// native function that initializes an array  
void native_function(int* p) {  
   for(int i = 0 ; i < 10 ; i++)  
    p[i] = i;  
}  
#pragma managed  
  
public ref class A {  
private:  
   array<int>^ arr;   // CLR integer array  
  
public:  
   A() {  
      arr = gcnew array<int>(SIZE);  
   }  
  
   void load() {  
   pin_ptr<int> p = &arr[0];   // pin pointer to first element in arr  
   int* np = p;   // pointer to the first element in arr  
   native_function(np);   // pass pointer to native function  
   }  
  
   int sum() {  
      int total = 0;  
      for (int i = 0 ; i < SIZE ; i++)  
         total += arr[i];  
      return total;  
   }  
};  
  
int main() {  
   A^ a = gcnew A;  
   a->load();   // initialize managed array using the native function  
   Console::WriteLine(a->sum());  
}  
```  
  
 **Output**  
  
```Output  
45  
```  
  
 **Příklad**  
  
 Následující příklad ukazuje, že vnitřní ukazatel můžete převést na Připnutí ukazatelů a že návratový typ address-of – operátor (`&`) je vnitřní ukazatel operand je na spravované haldě.  
  
```  
// pin_ptr_2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct G {  
   G() : i(1) {}  
   int i;  
};  
  
ref struct H {  
   H() : j(2) {}  
   int j;  
};  
  
int main() {  
   G ^ g = gcnew G;   // g is a whole reference object pointer  
   H ^ h = gcnew H;  
  
   interior_ptr<int> l = &(g->i);   // l is interior pointer  
  
   pin_ptr<int> k = &(h->j);   // k is a pinning interior pointer  
  
   k = l;   // ok  
   Console::WriteLine(*k);  
};  
```  
  
 **Output**  
  
```Output  
1  
```  
  
 **Příklad**  
  
 Následující příklad ukazuje, že Připnutí ukazatel lze převést na jiný typ.  
  
```  
// pin_ptr_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref class ManagedType {  
public:  
   int i;  
};  
  
int main() {  
   ManagedType ^mt = gcnew ManagedType;  
   pin_ptr<int> pt = &mt->i;  
   *pt = 8;  
   Console::WriteLine(mt->i);  
  
   char *pc = ( char* ) pt;  
   *pc = 255;  
   Console::WriteLine(mt->i);  
}  
```  
  
 **Output**  
  
```Output  
8  
255  
```