---
title: pin_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- pin_ptr_cpp
- stdcli::language::pin_ptr
- pin_ptr
helpviewer_keywords:
- pinning pointers
- pin_ptr keyword [C++]
ms.assetid: 6c2e6c73-4ec2-4dce-8e1f-ccf3a9f9d0aa
ms.openlocfilehash: 920135943c9dfb46b00ee6ceb2535fde128dffb0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172032"
---
# <a name="pin_ptr-ccli"></a>pin_ptr (C++/CLI)

Deklaruje *ukazatel připnutí*, který se používá pouze s modulem CLR (Common Language Runtime).

## <a name="all-runtimes"></a>Všechny moduly runtime

(Žádné poznámky k této funkci jazyka se nevztahují na všechny moduly runtime.)

## <a name="windows-runtime"></a>prostředí Windows Runtime

(Tato funkce jazyka není podporována v prostředí Windows Runtime.)

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

*Ukazatel připnutí* je vnitřní ukazatel, který brání tomu, aby se objekt odkazoval na haldu uvolňování paměti. To znamená, že hodnota ukazatele připnutí není upravena modulem CLR (Common Language Runtime). To je vyžadováno, Pokud předáte adresu spravované třídy do nespravované funkce tak, aby se adresa neočekávaně nezměnila během překladu nespravovaného volání funkce.

### <a name="syntax"></a>Syntaxe

```cpp
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;
```

### <a name="parameters"></a>Parametry

*cv_qualifier*<br/>
kvalifikátory **const** nebo **volatile** . Ve výchozím nastavení je ukazatel připnutí **nestálý**. Je redundantní, ale není chyba deklarovat ukazatel připnutí na **volatili**.

*type*<br/>
Typ *inicializátoru*

*var*<br/>
Název proměnné **pin_ptr** .

*inicializátor*<br/>
Člen typu odkazu, element spravovaného pole nebo jakýkoli jiný objekt, který lze přiřadit nativnímu ukazateli.

### <a name="remarks"></a>Poznámky

**Pin_ptr** představuje nadmnožinu funkcí nativního ukazatele. Z toho důvodu může být vše, co lze přiřadit nativnímu ukazateli, přiřazeno také **pin_ptr**. Vnitřní ukazatel je povolen pro provádění stejné sady operací jako nativní ukazatelů, včetně porovnání a aritmetické operace s ukazatelem.

Objekt nebo dílčí objekt spravované třídy lze připnout, v takovém případě modul common language runtime ho nebude přesouvat během uvolňování paměti. Hlavní použití tohoto parametru je předat ukazatel na spravovaná data jako skutečný parametr nespravovaného volání funkce. Během cyklu shromažďování bude modul runtime kontrolovat metadata vytvořená pro ukazatel připnutí a nepřesouvá položku, na kterou odkazuje.

Připnutí objektu také připnutím jeho hodnotových polí; To znamená, že pole primitivního nebo hodnotového typu. Nicméně pole deklarovaná sledovacím popisovačem (`%`) nejsou připnutá.

Připnutí dílčího objektu definovaného ve spravovaném objektu má vliv na připnutí celého objektu.

Pokud je ukazatel připnutí přiřazený k ukazateli na novou hodnotu, předchozí instance, na kterou ukazuje, již není považována za připnutý.

Objekt je připnutý pouze v případě, že k němu **pin_ptr** odkazuje. Objekt již není připnuté, když se ukazatel připnutí stane mimo rozsah, nebo je nastaven na [nullptr](nullptr-cpp-component-extensions.md). Po **pin_ptr** mimo rozsah může být objekt, který byl připnutý, přesunut v haldě systémem uvolňování paměti. Všechny nativní ukazatele, které stále odkazují na objekt, nebudou aktualizovány a zrušení odkazování jednoho z nich by mohlo vyvolat neobnovitelné výjimky.

Nejsou-li žádné ukazatele připnutí odkazovány na objekt (všechny ukazatele připnutí byly předány z rozsahu, byly přiřazeny k ukazateli na jiné objekty nebo byly přiřazeny [nullptr](nullptr-cpp-component-extensions.md)), je zaručeno, že objekt nebude připnuté.

Ukazatel připnutí může ukazovat na popisovač odkazu, na typ hodnoty nebo na popisovač zabaleného typu, člen spravovaného typu nebo element spravovaného pole. Nemůže odkazovat na typ odkazu.

Převzetí adresy **pin_ptr** , která odkazuje na nativní objekt, způsobí nedefinované chování.

Ukazatele připnutí můžou být v zásobníku deklarované jenom jako nestatické lokální proměnné.

Ukazatele připnutí nelze použít jako:

- funkční parametry

- návratový typ funkce

- člen třídy

- cílový typ přetypování.

**pin_ptr** je v oboru názvů `cli`. Další informace najdete v tématu [obory názvů Platform, default a CLI](platform-default-and-cli-namespaces-cpp-component-extensions.md).

Další informace o vnitřních ukazatelích naleznete v tématu [interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md).

Další informace o připnutí ukazatelů naleznete v tématu [How to: připnout ukazatele a Arrays](how-to-pin-pointers-and-arrays.md) a [How to: Declare ukazatelé a typy hodnot připnutí](how-to-declare-pinning-pointers-and-value-types.md).

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad používá **pin_ptr** k omezení pozice prvního prvku pole.

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

Následující příklad ukazuje, že vnitřní ukazatel lze převést na ukazatel připnutí a že návratový typ operátoru address-of (`&`) je vnitřní ukazatel, pokud je operand na spravované haldě.

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

Následující příklad ukazuje, že ukazatel připnutí lze přetypovat na jiný typ.

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
