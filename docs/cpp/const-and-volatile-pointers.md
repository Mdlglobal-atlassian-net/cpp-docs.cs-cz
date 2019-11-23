---
title: const a volatile – ukazatele
ms.date: 11/19/2019
helpviewer_keywords:
- volatile keyword [C++], and pointers
- pointers, and const
- pointers, and volatile
- const keyword [C++], volatile pointers
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
ms.openlocfilehash: c0aafde9070275abcb270710e2d4a7a8d9806267
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246632"
---
# <a name="const-and-volatile-pointers"></a>const a volatile – ukazatele

Klíčová slova [const](const-cpp.md) a [volatile](volatile-cpp.md) mění způsob, jakým jsou zpracovány ukazatele. Klíčové slovo **const** určuje, že ukazatel po inicializaci nemůže být změněn; ukazatel je chráněn před úpravou poté.

Klíčové slovo **volatile** určuje, že hodnotu přidruženou k názvu, který následuje, lze upravit pomocí jiných akcí než těch v uživatelské aplikaci. Proto klíčové slovo **volatile** je užitečné pro deklarování objektů ve sdílené paměti, ke kterým je možné přistupovat pomocí více procesů nebo globálních datových oblastí používaných pro komunikaci s rutinami služby přerušení.

Pokud je název deklarován jako **volatile**, kompilátor znovu načte hodnotu z paměti pokaždé, když k ní program přistupuje. Tím jsou výrazně omezeny možné optimalizace. Pokud však může dojít k nečekané změně stavu objektu, jde o jediný způsob, jak lze zajistit předvídatelný výkon programu.

Chcete-li deklarovat objekt, na který odkazoval ukazatel jako **const** nebo **volatile**, použijte deklaraci formuláře:

```cpp
const char *cpch;
volatile char *vpch;
```

Chcete-li deklarovat hodnotu ukazatele – tj. skutečnou adresu uloženou v ukazateli – jako **const** nebo **volatili**, použijte deklaraci formuláře:

```cpp
char * const pchc;
char * volatile pchv;
```

C++ Jazyk zabraňuje přiřazení, která umožňují změnu objektu nebo ukazatele deklarovaného jako **const**. Taková přiřazení by odstranila informaci, s níž byl objekt nebo ukazatel deklarován, a porušila by tak záměr původní deklarace. Vezměte v úvahu následující deklarace:

```cpp
const char cch = 'A';
char ch = 'B';
```

Vzhledem k předchozím deklaracím dvou objektů (`cch`typu **const char**a `ch`typu **Char)** jsou následující deklarace/inicializace platné:

```cpp
const char *pch1 = &cch;
const char *const pch4 = &cch;
const char *pch5 = &ch;
char *pch6 = &ch;
char *const pch7 = &ch;
const char *const pch8 = &ch;
```

Následující deklarace či inicializace jsou chybné.

```cpp
char *pch2 = &cch;   // Error
char *const pch3 = &cch;   // Error
```

Deklarace proměnné `pch2` deklaruje ukazatel, pomocí kterého lze upravit konstantní objekt, a proto není povolena. Deklarace `pch3` určuje, zda je ukazatel konstantní, nikoli objekt; deklarace není povolena ze stejného důvodu, že deklarace `pch2` není povolena.

Následujících osm přiřazení ukazuje přiřazování pomocí ukazatele a změnu hodnoty ukazatele z předchozích deklarací. Pro tuto chvíli předpokládejme, že pro proměnné `pch1` až `pch8` byla inicializace správná.

```cpp
*pch1 = 'A';  // Error: object declared const
pch1 = &ch;   // OK: pointer not declared const
*pch2 = 'A';  // OK: normal pointer
pch2 = &ch;   // OK: normal pointer
*pch3 = 'A';  // OK: object not declared const
pch3 = &ch;   // Error: pointer declared const
*pch4 = 'A';  // Error: object declared const
pch4 = &ch;   // Error: pointer declared const
```

Ukazatele deklarované jako **nestálé**nebo jako kombinace **const** a **volatile**dodržují stejná pravidla.

Ukazatele na objekty **const** jsou často používány v deklaracích funkcí následujícím způsobem:

```cpp
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );
```

Předchozí příkaz deklaruje funkci, [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md), kde dva ze tří argumentů jsou typu ukazatel na **char**. Vzhledem k tomu, že argumenty jsou předány odkazem a nikoli hodnotou, funkce by byla volná pro úpravu `strDestination` a `strSource`, pokud `strSource` nebyla deklarována jako **const**. Deklarace `strSource` jako **const** zaručí volajícímu, že `strSource` nemůže změnit volaná funkce.

> [!NOTE]
> Vzhledem k tomu, že existuje standardní převod z *typename* <strong>\*</strong> na **const** *TypeName* <strong>\*</strong>, je právní předávat argument typu `char *` do [strcpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md). Opačně však není pravda; neexistuje žádný implicitní převod pro odebrání atributu **const** z objektu nebo ukazatele.

Ukazatel **const** daného typu lze přiřadit k ukazateli stejného typu. Ukazatel, který není **const** , však nelze přiřadit k ukazateli **const** . Následující kód ukazuje správná i nesprávná přiřazení:

```cpp
// const_pointer.cpp
int *const cpObject = 0;
int *pObject;

int main() {
pObject = cpObject;
cpObject = pObject;   // C3892
}
```

Následující příklad ukazuje, jak deklarovat objekt jako const, pracujete-li s ukazatelem na ukazatel na objekt.

```cpp
// const_pointer2.cpp
struct X {
   X(int i) : m_i(i) { }
   int m_i;
};

int main() {
   // correct
   const X cx(10);
   const X * pcx = &cx;
   const X ** ppcx = &pcx;

   // also correct
   X const cx2(20);
   X const * pcx2 = &cx2;
   X const ** ppcx2 = &pcx2;
}
```

## <a name="see-also"></a>Viz také:

[Ukazatele](pointers-cpp.md)
[nezpracovaných ukazatelů](raw-pointers.md)