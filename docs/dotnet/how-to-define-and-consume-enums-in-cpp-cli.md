---
title: 'Postupy: Definice a používání výčtů v C++vyhodnocovací'
ms.date: 11/04/2016
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
ms.openlocfilehash: 9787b7b96f83b2926c65209254c88eb56fe1a8ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387380"
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>Postupy: Definice a používání výčtů v C++vyhodnocovací

Toto téma popisuje výčtů v C++vyhodnocovací.

## <a name="specifying-the-underlying-type-of-an-enum"></a>Zadání podkladového typu výčtu

Ve výchozím nastavení, je základní typ výčtu `int`.  Můžete však určit typ, který má být podepsané nebo nepodepsané formy `int`, `short`, `long`, `__int32`, nebo `__int64`.  Můžete také použít `char`.

```
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

**Output**

```Output
sun
0
1
2
```

## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>Jak převést mezi spravovanými a standardními výčty

Neexistuje žádný standardní převod mezi výčet a celočíselného typu; přetypování je povinný.

```
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

**Output**

```Output
a and day2 are the same
```

## <a name="operators-and-enums"></a>Operátory a výčty

Následující operátory jsou platné pro výčty v C++vyhodnocovací:

|Operátor|
|--------------|
|== != \< > \<= >=|
|+ -|
|&#124; ^ & ~|
|++ --|
|sizeof|

Operátory &#124; ^ & ~ ++--je definovaná pouze pro výčty celočíselný základní typy, nikoli včetně bool.  Oba operandy musí být typu výčtu.

Kompilátor nemá žádné statické nebo dynamické kontrolu výsledku operace výčtu; operace můžou výsledkem hodnota není v rozsahu výčtu platná enumerátory.

> [!NOTE]
>  C ++ 11 zavádí výčet typů třídy v nespravovaném kódu, které se můžou výrazně lišit od třídy spravovaného výčtu v C++vyhodnocovací. Konkrétně se na typ třídy C ++ 11 výčtu nepodporuje stejné operátory jako typ třídy spravovaného výčtu v C++vyhodnocovací, a C++/CLI zdrojový kód musí poskytovat usnadnění specifikátor v spravovaného výčtu deklarace tříd aby bylo možné odlišit od nespravované (C ++ 11) deklarace třídy výčtu. Další informace o výčet tříd v C++vyhodnocovací, C++/CX a C ++ 11, najdete v části [výčet tříd](../extensions/enum-class-cpp-component-extensions.md).

```
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

```
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

**Output**

```Output
4
1
True
```

## <a name="see-also"></a>Viz také:

[enum class](../extensions/enum-class-cpp-component-extensions.md)
