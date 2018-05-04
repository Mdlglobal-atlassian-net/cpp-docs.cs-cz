---
title: Zarovnání (deklarace C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f39fe0cf3706a67e2aa42aa89de5914808e9cec
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="alignment-c-declarations"></a>Zarovnání (deklarace C++)
Jedna z nízké úrovně funkcí jazyka C++, je možnost určit přesné zarovnání objektů v paměti, aby maximální využití výhod architektura konkrétní hardware. Ve výchozím nastavení kompilátoru zarovnán členy třídy a struktury na jejich velikost: bool a char je zarovnán jeden bajt hranice, krátké na dva bajty, int na čtyř bajtů, dlouho, double a long double na 8 bajtů. Ve většině scénářů máte nikdy dělat starosti s zarovnání, protože výchozí zarovnání již optimální. V některých případech ale můžete dosáhnout výrazné vylepšení výkonu, nebo úspory paměti zadáním vlastních zarovnání pro datové struktury. Před Visual Studio 2015 se používá __alignof – klíčová slova specifická pro společnost Microsoft a declspec(alignas) k určení zarovnání větší než výchozí. Spouštění v sadě Visual Studio 2015 by měl používat C ++ 11 standardní klíčová slova [alignof a alignas](../cpp/alignof-and-alignas-cpp.md) pro přenositelnost maximální kódu. Nové klíčová slova chovají stejným způsobem pod pokličkou jako rozšíření specifické pro společnost Microsoft a v dokumentaci k tato rozšíření platí také pro nové klíčová slova. V tématu [__alignof – operátor](../cpp/alignof-operator.md) a [zarovnat](../cpp/align-cpp.md) Další informace. Standardní C++ neurčuje okolních chování pro zarovnání na hranicích menší než výchozí nastavení kompilátoru pro cílovou platformu, takže potřebujete použít Microsoft #pragma [pack](../preprocessor/pack.md) v takovém případě.  
  
 Poskytuje standardní knihovna C++ [aligned_storage – třída](../standard-library/aligned-storage-class.md) pro přidělování paměti pro datové struktury s vlastní zarovnání a [aligned_union – třída](../standard-library/aligned-union-class.md) pro určení zarovnání sjednocení s Destruktory nebo netriviální konstruktory.  
  
## <a name="about-alignment"></a>O zarovnání  
 Zarovnání je vlastností adresu paměti, vyjádřené jako adresu číselné modulo power 2. Například adresa 0x0001103F modulo 4 je 3; tuto adresu říká, že je pro zarovnání na 4n + 3, kde 4 udává zvolené power 2. Zarovnání adresu závisí na zvolené power dva. Stejnou adresu modulo 8 je 7. Adresu říká, že je pro zarovnání na X, pokud je jeho zarovnání Xn + 0.  
  
 Procesory spouštění instrukcí které pracují na data uložená v paměti a data jsou označených adresami v paměti. Kromě jeho adresy jeden datum také má velikost. Datum je volána přirozeně zarovnané, pokud jeho adresy je zarovnán na velikost a chybně zarovnaných jinak. Pokud je adresa použitá pro jeho rozpoznání je zarovnána na 8 například přirozeně zarovnána 8 bajtů dat s plovoucí desetinnou čárkou.  
  
 Kompilátoru zpracování dat alignmentDevice kompilátory pokus o přidělení data způsobem, který brání chybné zarovnání data.  
  
 Jednoduché datové typy kompilátor přiřadí adresy, které jsou násobky velikost v bajtech datového typu. Proto kompilátor přiřazuje adresy proměnné typu long, které jsou násobky čtyři, nastavení bitů dolní dvě adresy na nulu.  
  
 Kromě toho kompilátor ohraničí struktury v tak, aby přirozeně každý prvek struktury. Vezměte v úvahu x_ struktura struktura v následujícím příkladu kódu:  
  
```  
struct x_  
{  
   char a;     // 1 byte  
   int b;      // 4 bytes  
   short c;    // 2 bytes  
   char d;     // 1 byte  
} MyStruct;  
  
```  
  
 Kompilátor ohraničí tato struktura přirozeně vynutit zarovnání.  
  
 Následující příklad kódu ukazuje, jak kompilátor umístí vyplněný struktury v paměti: kopírování  
  
```  
// Shows the actual memory layout  
struct x_  
{  
   char a;            // 1 byte  
   char _pad0[3];     // padding to put 'b' on 4-byte boundary  
   int b;            // 4 bytes  
   short c;          // 2 bytes  
   char d;           // 1 byte  
   char _pad1[1];    // padding to make sizeof(x_) multiple of 4  
}  
  
```  
  
1.  Obě deklarace vrátí sizeof(struct x_) 12 bajtů.  
  
2.  Druhý deklarace obsahuje dva elementy odsazení:  
  
3.  Char – _pad0 [3], chcete-li zarovnat člen b int na hranici čtyř bajtů  
  
4.  Char – _pad1 [1], chcete-li zarovnat elementy pole _x struktura struktura panelu [3];  
  
5.  Odsazení zarovnává elementy panelu [3] způsobem, který umožňuje přirozené přístup.  
  
 Následující příklad kódu ukazuje na panelu rozložení [3] pole:  
  
```  
adr offset   element  
------   -------  
0x0000   char a;         // bar[0]  
0x0001   char pad0[3];  
0x0004   int b;  
0x0008   short c;  
0x000a   char d;  
0x000b   char _pad1[1];  
  
0x000c   char a;         // bar[1]  
0x000d   char _pad0[3];  
0x0010   int b;  
0x0014   short c;  
0x0016   char d;  
0x0017   char _pad1[1];  
  
0x0018   char a;         // bar[2]  
0x0019   char _pad0[3];  
0x001c   int b;  
0x0020   short c;  
0x0022   char d;  
0x0023   char _pad1[1];  
  
```  
  
## <a name="see-also"></a>Viz také  
 [Zarovnání struktury dat](http://en.wikipedia.org/wiki/Data_structure_alignment)