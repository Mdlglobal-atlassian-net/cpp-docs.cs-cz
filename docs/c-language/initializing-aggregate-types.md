---
title: Inicializace typů agregace | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- aggregate types [C++]
- union keyword [C], declarations
- types [C], initializing
- union keyword [C]
- aggregates [C++], initializing
ms.assetid: a8f8ed75-39db-4592-93b9-d3920d915810
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c12ece1767c73e94551072532bfde6b36650bca9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="initializing-aggregate-types"></a>Inicializace typů agregace
Typ "aggregate" je struktury, sjednocení nebo typ pole. Pokud typ agregace obsahuje členy typů agregace, použít pravidla inicializace rekurzivně.  
  
## <a name="syntax"></a>Syntaxe  
 *Inicializátor*:  
 **{***inicializátoru seznamu***}** / * pro inicializace agregace \*/  
  
 **{***inicializátoru seznamu***,}**  
  
 *inicializátoru seznamu*:  
 *Inicializátor*  
  
 *inicializátoru seznamu***,***inicializátoru*  
  
 *Inicializátoru seznamu* je seznam inicializátory oddělených čárkami. Každý inicializátoru v seznamu je buď konstantní výraz nebo seznam inicializátor. Proto mohou být vnořené inicializační seznamy. Tento formulář je užitečné pro inicializaci agregační členy agregační typu, jak je znázorněno v příkladech v této části. Ale pokud inicializátoru pro automatické identifikátor jeden výraz, se nemusí být konstantní výraz; jenom musí mít příslušného typu pro přiřazení k identifikátoru.  
  
 Pro každý inicializátoru seznamu hodnot konstantní výrazy přiřazená, v pořadí, na odpovídající členy agregační proměnné.  
  
 Pokud *inicializátoru seznamu* má méně hodnoty než typ agregace, zbývající členy nebo elementy typu agregace jsou inicializovány na hodnotu 0. Počáteční hodnota Automatické identifikátoru inicializovat není explicitně není definován. Pokud *inicializátoru seznamu* má více hodnot než typ agregace, dojde k chybě. Tato pravidla vztahují na všechny seznamy inicializátoru vložená a také na agregace jako celek.  
  
 Do struktury inicializátoru je výraz stejného typu nebo seznam inicializátory jeho členů uzavřený do složených závorek (**{}**). Nepojmenované bit pole členů nejsou inicializovány.  
  
 Při inicializaci sjednocení *inicializátoru seznamu* musí být jediný konstantní výraz. První člen sjednocení přiřazena hodnota konstantní výraz.  
  
 Pokud pole má neznámý velikost, počet inicializátory Určuje velikost pole a její typ se změní na dokončení. Neexistuje žádný způsob, chcete-li určit opakování inicializátoru v jazyce C nebo k chybě při inicializaci element uprostřed pole bez zadání také všechny předchozí hodnoty. Pokud potřebujete tuto operaci v programu, zápisu rutiny v jazyce sestavení.  
  
 Všimněte si, že počet inicializátory můžete nastavit velikost pole:  
  
```  
int x[ ] = { 0, 1, 2 }  
```  
  
 Pokud zadáte velikost a poskytnout nesprávný počet inicializátory, ale kompilátor vygeneruje chybu.  
  
 **Konkrétní Microsoft**  
  
 Maximální velikost pole je definována **size_t –**. Definované v záhlaví souboru STDDEF. H, **size_t –** je `unsigned int` s rozsahem 0x00000000 k 0x7CFFFFFF.  
  
 **Konkrétní Microsoft END**  
  
## <a name="examples"></a>Příklady  
 Tento příklad ukazuje inicializátory pro pole.  
  
```  
int P[4][3] =   
{  
    { 1, 1, 1 },  
    { 2, 2, 2 },  
    { 3, 3, 3,},  
    { 4, 4, 4,},  
};  
```  
  
 Tento příkaz deklaruje `P` jako čtyři tři pole a inicializuje prvky jeho první řádek na 1, elementy její druhý řádek na 2, a tak dále prostřednictvím čtvrtý řádek. Všimněte si, že seznam inicializátoru řádků třetí a čtvrtý obsahuje čárkami po poslední konstantní výraz. Poslední inicializátoru seznamu (`{4, 4, 4,},`) je také oddělený čárkou. Tyto další čárkami jsou povolené, ale nejsou požadována; pouze čárkami, které oddělují konstantní výrazy od sebe navzájem a ty, které oddělení jeden seznam inicializátoru z jiné, je potřeba.  
  
 Pokud agregační člen má žádný seznam inicializátoru vložená, hodnoty jednoduše přiřazená, v pořadí, pro každého člena subaggregate. Proto je ekvivalentní následující inicializace v předchozím příkladu:  
  
```  
int P[4][3] =   
{  
   1, 1, 1, 2, 2, 2, 3, 3, 3, 4, 4, 4  
};  
```  
  
 Složené závorky může zobrazit i kolem jednotlivých inicializátory v seznamu a pomohou Upřesnit v předchozím příkladu.  
  
 Při inicializaci agregační proměnnou, musí být použít složené závorky a inicializátoru uvádí správně. Následující příklad ilustruje kompilátoru výklad složené závorky podrobněji:  
  
```  
typedef struct   
{  
    int n1, n2, n3;  
} triplet;  
  
triplet nlist[2][3] =   
{  
    { {  1, 2, 3 }, {  4, 5, 6 }, {  7, 8, 9 } },  /* Row 1 */  
    { { 10,11,12 }, { 13,14,15 }, { 16,17,18 } }   /* Row 2 */  
};  
```  
  
 V tomto příkladu `nlist` je deklarován jako pole 2 3 struktur, každá struktura má tři členy. Řádek 1 inicializace přiřadí první řádek hodnot `nlist`, a to takto:  
  
1.  První levé závorky na řádku 1 signály kompilátor této inicializace první agregační členem `nlist` (tedy `nlist[0]`) je začátku.  
  
2.  Druhý levé závorky označuje, že inicializace první agregační členem `nlist[0]` (to znamená, struktura v `nlist[0][0]`) je začátku.  
  
3.  První pravé složené závorce končí inicializace struktury `nlist[0][0]`; další levé závorky spustí inicializace `nlist[0][1]`.  
  
4.  Tento proces pokračuje v až do konce řádku, které končí pravé složené závorce správné inicializace `nlist[0]`.  
  
 Řádek 2 přiřadí hodnoty do druhého řádku `nlist` podobným způsobem. Všimněte si, že vnější sady složené závorky obklopuje inicializátory v řádcích 1 a 2 jsou povinné. Následující konstrukce, která vynechá vnější složených závorek, způsobí chybu:  
  
```  
triplet nlist[2][3] =  /* THIS CAUSES AN ERROR */  
{  
     {  1, 2, 3 },{  4, 5, 6 },{  7, 8, 9 },   /* Line 1 */  
     { 10,11,12 },{ 13,14,15 },{ 16,17,18 }    /* Line 2 */  
};  
```  
  
 V této konstrukce spustí první levé závorky na řádku 1 inicializace `nlist[0]`, což je pole tři struktury. Hodnoty 1, 2 a 3 přiřazené k tři členy první struktury. Po inicializaci (po hodnotě 3) došlo k další pravé složené závorce `nlist[0]` dokončení, a dva zbývající struktury v poli tři struktura není inicializován automaticky na hodnotu 0. Podobně `{ 4,5,6 }` inicializuje první struktury v druhém řádku `nlist`. Zbývající dvě struktury `nlist[1]` jsou nastavena na hodnotu 0. Když kompilátor narazí další inicializátoru seznamu ( `{ 7,8,9 }` ), pokusí se inicializovat `nlist[2]`. Vzhledem k tomu `nlist` má pouze dva řádky, výsledkem bude chyba, tento pokus.  
  
 V této další příklad tří `int` členy `x` inicializovány na 1, 2 a 3, v uvedeném pořadí.  
  
```  
struct list   
{  
    int i, j, k;  
    float m[2][3];  
} x = {  
        1,  
        2,  
        3,  
       {4.0, 4.0, 4.0}  
      };  
```  
  
 V `list` struktura výše, tři prvky v prvním řádku `m` jsou inicializovány 4.0; elementy zbývající řádku `m` jsou inicializovány 0,0 ve výchozím nastavení.  
  
```  
union  
{  
    char x[2][3];  
    int i, j, k;  
} y = { {  
            {'1'},  
            {'4'}   
        }  
      };  
```  
  
 Proměnnou union `y`, v tomto příkladu je inicializován. První prvek sjednocení je pole, tak, aby inicializátoru inicializátoru agregační. V seznamu inicializátoru `{'1'}` přiřazuje hodnoty na první řádek pole. Vzhledem k tomu, že v seznamu se zobrazí pouze jednu hodnotu, je inicializováno element v první sloupec znak `1`, a zbývající dva elementy v řádku není inicializován na hodnotu 0 ve výchozím nastavení. Podobně první prvek druhého řádku `x` je inicializováno znak `4`, a zbývající dva elementy v řádku není inicializován na hodnotu 0.  
  
## <a name="see-also"></a>Viz také  
 [Inicializace](../c-language/initialization.md)