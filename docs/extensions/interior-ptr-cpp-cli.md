---
title: interior_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- stdcli::language::interior_ptr
- interior_ptr_cpp
- interior_ptr
helpviewer_keywords:
- interior_ptr keyword [C++]
ms.assetid: 25160f74-569e-492d-9e3c-67ece7486baa
ms.openlocfilehash: 264ac0a56996b0dcbeeb64246623eca1a3fc73ff
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172149"
---
# <a name="interior_ptr-ccli"></a>interior_ptr (C++/CLI)

*Vnitřní ukazatel* deklaruje ukazatel na typ odkazu, ale ne na samotný objekt. Vnitřní ukazatel může ukazovat na odkazový popisovač, hodnotový typ, zabalený popisovač typu, člen spravovaného typu nebo na element spravovaného pole.

## <a name="all-runtimes"></a>Všechny moduly runtime

(Žádné poznámky k této funkci jazyka se nevztahují na všechny moduly runtime.)

## <a name="windows-runtime"></a>prostředí Windows Runtime

(Pro tuto funkci jazyka neexistují žádné poznámky, které platí jenom pro prostředí Windows Runtime.)

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/ZW`

## <a name="common-language-runtime"></a>CLR (Common Language Runtime)

Následující příklad syntaxe ukazuje vnitřní ukazatel.

### <a name="syntax"></a>Syntaxe

```cpp
cli::interior_ptr<cv_qualifier type> var = &initializer;
```

### <a name="parameters"></a>Parametry

*cv_qualifier*<br/>
kvalifikátory **const** nebo **volatile** .

*type*<br/>
Typ *inicializátoru*

*var*<br/>
Název proměnné **interior_ptr** .

*inicializátor*<br/>
Člen typu odkazu, element spravovaného pole nebo jakýkoli jiný objekt, který lze přiřadit nativnímu ukazateli.

### <a name="remarks"></a>Poznámky

Nativní ukazatel není schopný sledovat položku jako změnu umístění na spravované haldě, která je výsledkem přesunutí instancí objektu uvolňování paměti. Aby ukazatel správně odkazoval na instanci, modul runtime musí aktualizovat ukazatel na nově umístěný objekt.

**Interior_ptr** představuje nadmnožinu funkcí nativního ukazatele.  Proto může být cokoli, co může být přiřazeno k nativnímu ukazateli, přiřazeno také **interior_ptr**.  Vnitřní ukazatel je povolen pro provádění stejné sady operací jako nativní ukazatelů, včetně porovnání a aritmetické operace s ukazatelem.

Vnitřní ukazatel se dá deklarovat jenom v zásobníku.  Vnitřní ukazatel nelze deklarovat jako člen třídy.

Vzhledem k tomu, že vnitřní ukazatele existují pouze v zásobníku, přičemž adresa vnitřního ukazatele vypočítá nespravovaný ukazatel.

**interior_ptr** má implicitní převod na **bool**, který umožňuje použití v podmíněných příkazech.

Informace o tom, jak deklarovat vnitřní ukazatel, který odkazuje na objekt, který nelze přesunout na haldu uvolňování paměti, naleznete v tématu [pin_ptr](pin-ptr-cpp-cli.md).

**interior_ptr** je v oboru názvů CLI.  Další informace najdete v tématu [obory názvů Platform, default a CLI](platform-default-and-cli-namespaces-cpp-component-extensions.md) .

Další informace o vnitřních ukazatelích naleznete v tématu.

- [Postupy: Deklarace a použití vnitřních ukazatelů a spravovaných polí (C++/CLI)](how-to-declare-and-use-interior-pointers-and-managed-arrays-cpp-cli.md)

- [Postupy: Deklarace hodnotových typů s použitím klíčového slova interior_ptr (C++/CLI)](how-to-declare-value-types-with-the-interior-ptr-keyword-cpp-cli.md)

- [Postupy: Přetížení funkcí s vnitřními a nativními ukazateli (C++/CLI)](how-to-overload-functions-with-interior-pointers-and-native-pointers-cpp-cli.md)

- [Postupy: Deklarace vnitřních ukazatelů s použitím klíčového slova const (C++/CLI)](how-to-declare-interior-pointers-with-the-const-keyword-cpp-cli.md)

### <a name="requirements"></a>Požadavky

Možnost kompilátoru: `/clr`

### <a name="examples"></a>Příklady

Následující příklad ukazuje, jak deklarovat a použít vnitřní ukazatel na typ odkazu.

```cpp
// interior_ptr.cpp
// compile with: /clr
using namespace System;

ref class MyClass {
public:
   int data;
};

int main() {
   MyClass ^ h_MyClass = gcnew MyClass;
   h_MyClass->data = 1;
   Console::WriteLine(h_MyClass->data);

   interior_ptr<int> p = &(h_MyClass->data);
   *p = 2;
   Console::WriteLine(h_MyClass->data);

   // alternatively
   interior_ptr<MyClass ^> p2 = &h_MyClass;
   (*p2)->data = 3;
   Console::WriteLine((*p2)->data);
}
```

```Output
1
2
3
```

## <a name="see-also"></a>Viz také

[Přípony komponent pro .NET a UPW](component-extensions-for-runtime-platforms.md)
