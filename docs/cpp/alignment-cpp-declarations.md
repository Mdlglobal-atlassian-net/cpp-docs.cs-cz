---
title: Zarovnání (deklarace C++) | Dokumentace Microsoftu
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
ms.openlocfilehash: 9031bea449968e22212c241b8418b505710cca8d
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408629"
---
# <a name="alignment-c-declarations"></a>Zarovnání (deklarace C++)
Jednou z nízké úrovně funkcí jazyka C++ je schopnost určit přesné zarovnání objektů v paměti maximálně využijí architektury konkrétní hardware. Ve výchozím nastavení, kompilátor zarovná členy třídy a struktury na jejich velikost: bool a char jsou zarovnány jeden hranice jeden bajt, short na dva bajty, int na čtyři bajty, long long double a long double na osm bajtů. Ve většině případů budete muset nikdy být obeznámeni s zarovnání, protože je již optimální výchozí zarovnání. V některých případech však můžete dosáhnout výrazné zlepšení výkonu, nebo úspory paměti tak, že zadáte vlastní zarovnání datových struktur. Visual Studio 2015 můžete použít klíčová slova __alignof specifických pro společnost Microsoft a declspec(alignas) k určení zarovnání větší než výchozí. Spuštění v sadě Visual Studio 2015 používejte C ++ 11 standard klíčových slov [alignof a alignas](../cpp/alignof-and-alignas-cpp.md) pro přenositelnost maximální kódu. Nová klíčová slova se chovají stejným způsobem pod pokličkou jako rozšíření specifické pro společnost Microsoft a v dokumentaci pro tato rozšíření platí také pro nová klíčová slova. Zobrazit [__alignof – operátor](../cpp/alignof-operator.md) a [zarovnat](../cpp/align-cpp.md) Další informace. Standard jazyka C++ neurčuje balení chování pro zarovnání na hranicích menší než výchozí nastavení kompilátoru pro cílovou platformu, takže budete stále muset použít Microsoft #pragma [pack](../preprocessor/pack.md) v takovém případě.  
  
 Poskytuje standardní knihovny C++ [aligned_storage – třída](../standard-library/aligned-storage-class.md) pro přidělení paměti pro datové struktury s vlastní zarovnání a [aligned_union – třída](../standard-library/aligned-union-class.md) pro určení zarovnání pro sjednocení s netriviálními konstruktory a destruktory.  
  
## <a name="about-alignment"></a>Informace o zarovnání  
 Zarovnání je vlastností adresu paměti, vyjádřené jako číselné adresu modulo mocninou čísla 2. Například adresa 0x0001103F modulo 4 je 3; tuto adresu se říká, že pro zarovnání na 4n + 3, kde označuje zvolený Mocnina 2, 4. Zarovnání adresu závisí zvoleném mocninou čísla 2. Stejnou adresu modulo 8 je 7. Adresa se říká, že pro zarovnání na X, pokud je jeho zarovnání Xn + 0.  
  
 Procesory spouštění instrukcí, které pracují s daty uloženými v paměti a data jsou identifikována podle jejich adresy v paměti. Kromě jeho adresu jedné datum má také velikost. Datum je volána přirozeně zarovnané, pokud jeho adresu zarovnán na jejich velikost a chybně zarovnaných jinak. Pokud je adresa použitá k jeho identifikaci zarovnán na 8 například přirozeně zarovnána 8 bajtů datum s plovoucí desetinnou čárkou.  
  
 Kompilátor zpracování kompilátory alignmentDevice dat došlo k pokusu o přidělení data způsobem, který brání chybné data.  
  
 Pro jednoduché datové typy kompilátor přiřadí adresy, které jsou násobky velikost v bajtech datového typu. Proto kompilátor přiřadí adresy proměnné typu long, které jsou násobky čtyř, nastavení dva bity dolní adresy na nulu.  
  
 Kromě toho kompilátor vyplní struktury tak, aby přirozeně zarovná každý prvek struktury. Vezměte v úvahu x_ struktury struktura v následujícím příkladu kódu:  
  
```cpp 
struct x_  
{  
   char a;     // 1 byte  
   int b;      // 4 bytes  
   short c;    // 2 bytes  
   char d;     // 1 byte  
} MyStruct;  
  
```  
  
 Kompilátor vyplní tato struktura přirozeně vynutit zarovnání.  
  
 Následující příklad kódu ukazuje, jak kompilátor umístí vyplněný struktury v paměti: kopírování  
  
```cpp 
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
  
1.  Obě deklarace vrátit sizeof(struct x_) jako 12 bajtů.  
  
2.  Druhý deklarace obsahuje dva prvky odsazení:  
  
3.  Char – _pad0 [3] pro zarovnání členských b int na hranici čtyř bajtů  
  
4.  Char – _pad1 [1] pro zarovnání prvků pole struktury _x struktura panelu [3];  
  
5.  Odsazení se zarovná elementy panelu [3] způsobem, který umožňuje přístup k fyzické.  
  
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
  
## <a name="see-also"></a>Viz také:  
 [Zarovnání struktury dat](http://en.wikipedia.org/wiki/Data_structure_alignment)