---
title: pin_ptr (C + +/ CLI) | Dokumentace Microsoftu
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
ms.openlocfilehash: de7f4c94ec0d9cb5a9a57315ebda015b7737132c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392759"
---
# <a name="pinptr-ccli"></a>pin_ptr (C++/CLI)

Deklaruje *ukazatel Připnutí*, který se používá jenom s common language runtime.

## <a name="all-runtimes"></a>Všechny moduly runtime

(Neexistují žádné poznámky o této funkci jazyka, které platí pro všechny moduly runtime.)

## <a name="windows-runtime"></a>prostředí Windows Runtime

(Tato funkce jazyka není podporována v modulu Windows Runtime).

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

A *ukazatel Připnutí* vnitřní ukazatel, který brání objekt ukazuje získat přechodem na haldě uvolňování paměti. To znamená se nezmění hodnotu ukazatel Připnutí modulem common language runtime. To je potřeba při předání adresy spravovanou třídu nespravované funkci tak, aby během rozlišení nespravovanou funkci volání nezmění neočekávaně adresu.

### <a name="syntax"></a>Syntaxe

```cpp
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;
```

### <a name="parameters"></a>Parametry

*cv_qualifier*<br/>
**Const** nebo **volatile** kvalifikátory. Ve výchozím nastavení, je ukazatel Připnutí **volatile**. Je redundantní, ale ne o chybu deklarovat ukazatel Připnutí **volatile**.

*Typ*<br/>
Typ *inicializátor*.

*var*<br/>
Název **pin_ptr** proměnné.

*Inicializátor*<br/>
Člen typu odkazu, element spravovaného pole nebo jakýkoli jiný objekt, který můžete přiřadit na nativní ukazatel.

### <a name="remarks"></a>Poznámky

A **pin_ptr** představuje nadmnožinu funkcí nativní ukazatel. Proto cokoli, co je možné přiřadit na nativní ukazatel lze také přiřadit **pin_ptr**. Vnitřní ukazatel se nepovoluje provádět stejnou sadu operací, jako nativní ukazatele, včetně porovnání a aritmetiku ukazatele.

Objekt nebo podobjektu spravované třídy je možné připnout, v takovém případě common language runtime nepřesune během uvolňování paměti. Instančního objektu pomocí tohoto objektu je předat ukazatel spravovaných dat jako skutečný parametr nespravované funkci volání. Během cyklu shromažďování modul runtime bude kontrolovat metadat pro ukazatel Připnutí vytvořit a nepřesune, na který odkazuje na položku.

Připnutí objekt také vážou jeho hodnoty polí. To znamená, že pole primitivních nebo hodnota typu. Pole však deklaroval sledovací popisovač (`%`) nejsou připnuté.

Připnutí dílčí objekt definovaný v spravovaný objekt má za následek Připnutí celý objekt.

Pokud ukazatel Připnutí je přiřazena tak, aby odkazoval na novou hodnotu, předchozí instanci, na které je nelze nadále považovat za připnout.

Objekt je připnutá pouze při **pin_ptr** na ně odkazuje. Objekt je již ukotvena při jeho Připnutí ukazatel dostane mimo rozsah, nebo je nastaven na [nullptr](../windows/nullptr-cpp-component-extensions.md). Po **pin_ptr** překročí obor, objekt, který byla připnuta může přesunou v haldě systému uvolňování paměti. Všechny nativní ukazatele, které stále odkazují na objekt nebude aktualizován a zrušením odkazu jeden z nich může vyvolat výjimku neobnovitelná.

Pokud žádné přídavných ukazatelů ukazuje na objekt (všechny přídavných ukazatelů přestala být obor, byl znovu přiřazen tak, aby odkazoval na jiné objekty nebo byly přiřazeny [nullptr](../windows/nullptr-cpp-component-extensions.md)), je zaručeno, že objekt není možné připnout.

Odkaz na popisovač, typ hodnoty nebo popisovač zabalený typ, člen spravovaného typu nebo jeho element spravovaného pole může odkazovat ukazatel Připnutí. Nemůže odkazovat na typ odkazu.

Přebírání adresy **pin_ptr** , odkazuje na nativní objekt způsobí nedefinované chování.

Přídavných ukazatelů může deklarovat jenom jako nestatická místní proměnné v zásobníku.

Přídavných ukazatelů nelze použít jako:

- funkční parametry

- Návratový typ funkce

- člen třídy

- cílový typ přetypování.

**pin_ptr** probíhá `cli` oboru názvů. Další informace najdete v tématu [Platform, default a cli obory názvů](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md).

Další informace o vnitřních ukazatelů naleznete v tématu [interior_ptr (C + +/ CLI)](../windows/interior-ptr-cpp-cli.md).

Další informace o přídavné ukazatele, naleznete v tématu [jak: Pin ukazatelů a polí](../windows/how-to-pin-pointers-and-arrays.md) a [postupy: deklarování Připnutí ukazatelů a typů hodnot](../windows/how-to-declare-pinning-pointers-and-value-types.md).

### <a name="requirements"></a>Požadavky

– Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad používá **pin_ptr** omezit pozice prvního prvku pole.

```cpp
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

```Output
45
```

Následující příklad ukazuje, že vnitřní ukazatel lze převést na ukazatel Připnutí a návratový typ operátoru address-of (`&`) je vnitřní ukazatel operand je na spravované haldě.

```cpp
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

```Output
1
```

Následující příklad ukazuje, že ukazatel Připnutí lze převést na jiného typu.

```cpp
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

```Output
8
255
```