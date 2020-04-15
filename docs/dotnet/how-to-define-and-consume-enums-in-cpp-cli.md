---
title: 'Postupy: Definice a používání výčtů v jazyce C++/CLI'
ms.date: 11/04/2016
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
ms.openlocfilehash: cf3bb23069b2692c0ca4ce270a5b8060195becf7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370178"
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>Postupy: Definice a používání výčtů v jazyce C++/CLI

Toto téma popisuje výčty v jazyce C++/CLI.

## <a name="specifying-the-underlying-type-of-an-enum"></a>Určení základního typu výčtu

Ve výchozím nastavení je `int`základní typ výčtu .  Můžete však určit typ, který má být `int` `short`podepsán `long` `__int32`nebo `__int64`podepsán, formuláře , , , nebo .  Můžete také `char`použít .

```cpp
// mcppv2_enum_3.cpp
// compile with: /clr
public enum class day_char : char {sun, mon, tue, wed, thu, fri, sat};

int main() {
   // fully qualified names, enumerator not injected into scope
   day_char d = day_char::sun, e = day_char::mon;
   System::Console::WriteLine(d);
   char f = (char)d;
   System::Console::WriteLine(f);
   f = (char)e;
   System::Console::WriteLine(f);
   e = day_char::tue;
   f = (char)e;
   System::Console::WriteLine(f);
}
```

**Výstup**

```Output
sun
0
1
2
```

## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>Převod mezi spravovanými a standardními výčty

Neexistuje žádný standardní převod mezi výčtu a integrální typ; je vyžadováno obsazení.

```cpp
// mcppv2_enum_4.cpp
// compile with: /clr
enum class day {sun, mon, tue, wed, thu, fri, sat};
enum {sun, mon, tue, wed, thu, fri, sat} day2; // unnamed std enum

int main() {
   day a = day::sun;
   day2 = sun;
   if ((int)a == day2)
   // or...
   // if (a == (day)day2)
      System::Console::WriteLine("a and day2 are the same");
   else
      System::Console::WriteLine("a and day2 are not the same");
}
```

**Výstup**

```Output
a and day2 are the same
```

## <a name="operators-and-enums"></a>Operátory a výčty

Následující operátory jsou platné na výčty v jazyce C++/CLI:

|Operátor|
|--------------|
|== != \<  >  \<= >=|
|+ -|
|&#124; ^ & ~|
|++ --|
|sizeof|

Operátory &#124; ^ & ~ ++ -- jsou definovány pouze pro výčty s integrální základní typy, bez bool.  Oba operandy musí být typu výčtu.

Kompilátor neprovádí žádnou statickou nebo dynamickou kontrolu výsledku operace výčtu. operace může mít za následek hodnotu není v rozsahu platných výčtu výčtu.

> [!NOTE]
> C++ 11 zavádí výčtu typy tříd v nespravovaném kódu, které se výrazně liší od spravované třídy výčtu v Jazyce C++/CLI. Zejména typ třídy výčtu C++11 nepodporuje stejné operátory jako typ třídy spravovaného výčtu v jazyce C++/CLI a zdrojový kód C++/CLI musí poskytnout specifikátor přístupnosti ve spravovaných deklaracích tříd výčtu, aby je odlišil od nespravovaných deklarací tříd (C ++ 11). Další informace o výčtu tříd v C++/CLI, C++/CX a C++11, naleznete [v tématu výčtu třídy](../extensions/enum-class-cpp-component-extensions.md).

```cpp
// mcppv2_enum_5.cpp
// compile with: /clr
private enum class E { a, b } e, mask;
int main() {
   if ( e & mask )   // C2451 no E->bool conversion
      ;

   if ( ( e & mask ) != 0 )   // C3063 no operator!= (E, int)
      ;

   if ( ( e & mask ) != E() )   // OK
      ;
}
```

```cpp
// mcppv2_enum_6.cpp
// compile with: /clr
private enum class day : int {sun, mon};
enum : bool {sun = true, mon = false} day2;

int main() {
   day a = day::sun, b = day::mon;
   day2 = sun;

   System::Console::WriteLine(sizeof(a));
   System::Console::WriteLine(sizeof(day2));
   a++;
   System::Console::WriteLine(a == b);
}
```

**Výstup**

```Output
4
1
True
```

## <a name="see-also"></a>Viz také

[enum class](../extensions/enum-class-cpp-component-extensions.md)
