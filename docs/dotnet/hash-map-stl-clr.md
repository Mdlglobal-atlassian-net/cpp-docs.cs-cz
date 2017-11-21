---
title: "hash_map – (STL/CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_map
dev_langs: C++
helpviewer_keywords:
- <cliext/hash_map> header [STL/CLR]
- <hash_map> header [STL/CLR]
- hash_map class [STL/CLR]
ms.assetid: c3cfc69b-04c6-42ae-a30e-0eda953fe883
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: aae2ca596a04a6502fc50bc7ac2cb6344463f739
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="hashmap-stlclr"></a>hash_map (STL/CLR)
Šablony třídy popisuje objekt, který řídí různých délka pořadí elementů, která má obousměrný přístup. Použít metodu kontejneru `hash_map` ke správě pořadí elementů jako zatřiďovací tabulku, každý záznam tabulky, ukládání obousměrné propojené seznam uzlů a každý uzel ukládání jeden element. Element obsahuje klíč, pro řazení sekvenci a namapované hodnotu, kterou má význam pro pravé.  
  
 V popisu níže `GValue` je stejný jako:  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 kde:  
  
 `GKey`je stejný jako `Key` Pokud k tomu je typu ref, v takovém případě je`Key^`  
  
 `GMapped`je stejný jako `Mapped` Pokud k tomu je typu ref, v takovém případě je`Mapped^`  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class hash_map  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        System::Collections::Generic::IDictionary<Gkey, GMapped>,  
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>  
    { ..... };  
```  
  
#### <a name="parameters"></a>Parametry  
 Key  
 Typ elementu v řízené sekvenci komponenta klíče.  
  
 Mapovat  
 Typ elementu v řízené sekvenci další součásti.  
  
## <a name="members"></a>Členové  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[hash_map::const_iterator (STL/CLR)](../dotnet/hash-map-const-iterator-stl-clr.md)|Typ konstantního iterátoru řízené sekvence|  
|[hash_map::const_reference (STL/CLR)](../dotnet/hash-map-const-reference-stl-clr.md)|Typ konstantního odkazu na prvek|  
|[hash_map::const_reverse_iterator (STL/CLR)](../dotnet/hash-map-const-reverse-iterator-stl-clr.md)|Typ konstantní zpětné iterator pro řízené sekvenci.|  
|[hash_map::difference_type (STL/CLR)](../dotnet/hash-map-difference-type-stl-clr.md)|Typ (může být podepsaná) vzdálenost mezi dvěma prvky.|  
|[hash_map::generic_container (STL/CLR)](../dotnet/hash-map-generic-container-stl-clr.md)|Typ generické rozhraní pro kontejner.|  
|[hash_map::generic_iterator (STL/CLR)](../dotnet/hash-map-generic-iterator-stl-clr.md)|Typ iterace pro obecné rozhraní kontejneru.|  
|[hash_map::generic_reverse_iterator (STL/CLR)](../dotnet/hash-map-generic-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro obecné rozhraní kontejneru.|  
|[hash_map::generic_value (STL/CLR)](../dotnet/hash-map-generic-value-stl-clr.md)|Typ elementu pro obecné rozhraní kontejneru.|  
|[hash_map::hasher (STL/CLR)](../dotnet/hash-map-hasher-stl-clr.md)|Hash delegáta pro klíč.|  
|[hash_map::iterator (STL/CLR)](../dotnet/hash-map-iterator-stl-clr.md)|Typ iterátoru řízené sekvence|  
|[hash_map::key_compare (STL/CLR)](../dotnet/hash-map-key-compare-stl-clr.md)|Řazení delegáta pro dva klíče.|  
|[hash_map::key_type (STL/CLR)](../dotnet/hash-map-key-type-stl-clr.md)|Typ klíče řazení|  
|[hash_map::mapped_type (STL/CLR)](../dotnet/hash-map-mapped-type-stl-clr.md)|Typ namapované hodnotu přidruženou každý klíč.|  
|[hash_map::Reference (STL/CLR)](../dotnet/hash-map-reference-stl-clr.md)|Typ odkazu na prvek|  
|[hash_map::reverse_iterator (STL/CLR)](../dotnet/hash-map-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro řízené sekvenci.|  
|[hash_map::size_type (STL/CLR)](../dotnet/hash-map-size-type-stl-clr.md)|Typ (nezáporné) vzdálenost mezi dvěma prvky.|  
|[hash_map::value_compare (STL/CLR)](../dotnet/hash-map-value-compare-stl-clr.md)|Řazení delegáta pro dvě hodnoty elementu.|  
|[hash_map::value_type (STL/CLR)](../dotnet/hash-map-value-type-stl-clr.md)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[hash_map::begin (STL/CLR)](../dotnet/hash-map-begin-stl-clr.md)|Určuje začátek řízené sekvence.|  
|[hash_map::bucket_count (STL/CLR)](../dotnet/hash-map-bucket-count-stl-clr.md)|Spočítá počet intervalů.|  
|[hash_map::clear (STL/CLR)](../dotnet/hash-map-clear-stl-clr.md)|Odebere všechny prvky.|  
|[hash_map::Count (STL/CLR)](../dotnet/hash-map-count-stl-clr.md)|Vrátí počet prvků odpovídající zadaného klíče.|  
|[hash_map::Empty (STL/CLR)](../dotnet/hash-map-empty-stl-clr.md)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[hash_map::end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)|Určuje konec řízené sekvence.|  
|[hash_map::equal_range (STL/CLR)](../dotnet/hash-map-equal-range-stl-clr.md)|Najde rozsah, který odpovídá zadanému klíči.|  
|[hash_map::Erase (STL/CLR)](../dotnet/hash-map-erase-stl-clr.md)|Odebere prvky v určených pozicích.|  
|[hash_map::Find (STL/CLR)](../dotnet/hash-map-find-stl-clr.md)|Vyhledá prvek, který odpovídá zadanému klíči.|  
|[hash_map::hash_delegate (STL/CLR)](../dotnet/hash-map-hash-delegate-stl-clr.md)|Zkopíruje hash delegáta pro klíč.|  
|[hash_map::hash_map (STL/CLR)](../dotnet/hash-map-hash-map-stl-clr.md)|Sestaví objekt kontejneru.|  
|[hash_map::Insert (STL/CLR)](../dotnet/hash-map-insert-stl-clr.md)|Přidá prvky.|  
|[hash_map::key_comp (STL/CLR)](../dotnet/hash-map-key-comp-stl-clr.md)|Zkopíruje řazení delegáta pro dva klíče.|  
|[hash_map::load_factor (STL/CLR)](../dotnet/hash-map-load-factor-stl-clr.md)|Spočítá průměrný počet prvků na kbelík.|  
|[hash_map::lower_bound (STL/CLR)](../dotnet/hash-map-lower-bound-stl-clr.md)|Najde začátek rozsahu, který odpovídá zadaným klíčem.|  
|[hash_map::make_value (STL/CLR)](../dotnet/hash-map-make-value-stl-clr.md)|Vytvoří objekt hodnoty.|  
|[hash_map::max_load_factor (STL/CLR)](../dotnet/hash-map-max-load-factor-stl-clr.md)|Získá nebo nastaví maximální počet prvků na kbelík.|  
|[hash_map::rbegin (STL/CLR)](../dotnet/hash-map-rbegin-stl-clr.md)|Označuje začátek odstínech řízené sekvenci.|  
|[hash_map::rehash (STL/CLR)](../dotnet/hash-map-rehash-stl-clr.md)|Znovu vytvoří hashovací tabulku.|  
|[hash_map::rend (STL/CLR)](../dotnet/hash-map-rend-stl-clr.md)|Označuje konec odstínech řízené sekvenci.|  
|[hash_map::size (STL/CLR)](../dotnet/hash-map-size-stl-clr.md)|Spočítá počet prvků.|  
|[hash_map::swap (STL/CLR)](../dotnet/hash-map-swap-stl-clr.md)|Zamění obsah dvou kontejnerů.|  
|[hash_map::to_array (STL/CLR)](../dotnet/hash-map-to-array-stl-clr.md)|Zkopíruje řízené sekvenci do nové pole.|  
|[hash_map::upper_bound (STL/CLR)](../dotnet/hash-map-upper-bound-stl-clr.md)|Najde konec rozsahu, který odpovídá zadaným klíčem.|  
|[hash_map::value_comp (STL/CLR)](../dotnet/hash-map-value-comp-stl-clr.md)|Zkopíruje řazení delegáta pro dvě hodnoty elementu.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[hash_map::Operator = (STL/CLR)](../dotnet/hash-map-operator-assign-stl-clr.md)|Nahradí řízené sekvenci.|  
|[hash_map::Operator(STL/CLR)](../dotnet/hash-map-operator-stl-clr.md)|Klíč se mapuje na její přidružené hodnoty namapované.|  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicitní objekt.|  
|<xref:System.Collections.IEnumerable>|Pořadí pomocí elementů.|  
|<xref:System.Collections.ICollection>|Údržba skupiny elementů.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Pořadí prostřednictvím typové elementy.|  
|<xref:System.Collections.Generic.ICollection%601>|Údržba skupiny typové elementů.|  
|<xref:System.Collections.Generic.IDictionary%602>|Údržba skupiny {klíč a hodnotu} páry.|  
|IHash < klíč, hodnota >|Udržujte obecné kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt přiděluje a uvolní úložiště pro pořadí, které ovládá jako jednotlivé uzly v obousměrných odkazovaného seznamu. Objekt k urychlení přístupu, také udržuje různých délka pole ukazatele do seznamu (zatřiďovací tabulku), efektivně spravovat celý seznam jako posloupnost podřízených seznamů, nebo intervalů. Vloží elementy na bloku, který udržuje seřazené změnou propojení mezi uzly, nikdy zkopírováním obsah jednoho uzlu do jiného. To znamená, že můžete vložit a odeberte elementy volně bez narušení zbývající elementy.  
  
 Objekt řadí každé sady jimi řídí voláním objektu uložené delegáta typu [hash_set::key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md). Objekt uložené delegáta můžete zadat, když vytvoříte hash_set; Pokud zadáte žádný objekt delegáta, výchozí hodnota je porovnání `operator<=(key_type, key_type)`.  
  
 Přístup k objektu uložené delegáta voláním členské funkce [hash_set::key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)`()`. Takový objekt delegáta musí definovat ekvivalentní řazení mezi klíče typu [hash_set::key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md). To znamená, pro žádné dva klíče `X` a `Y`:  
  
 `key_comp()(X, Y)`Vrátí stejné logická hodnota způsobit při každém volání.  
  
 Pokud `key_comp()(X, Y) && key_comp()(Y, X)` má hodnotu true, pak `X` a `Y` se říká, že máte ekvivalentní řazení.  
  
 Jakékoli řazení pravidlo, které se chovají jako `operator<=(key_type, key_type)`, `operator>=(key_type, key_type)` nebo `operator==(key_type, key_type)` definuje eqivalent řazení.  
  
 Všimněte si, že kontejner je zajištěná pouze elementy jejichž klíče měly ekvivalentní řazení (a které hash na stejnou hodnotu celé číslo) sousedících v sadě. Na rozdíl od třídy šablony [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md), objekt třídy šablony `hash_map` zajišťuje, aby klíče pro všechny elementy byly jedinečné. (Žádná dva klíče mít ekvivalentní řazení.)  
  
 Určuje objekt sady, které by měl obsahovat k danému klíči řazení při volání objektu uložené delegáta typu [hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md). Přístup k této uložené objekt voláním členské funkce [hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) `()` získat celočíselná hodnota, která závisí na hodnotu klíče. Objekt uložené delegáta můžete zadat, když vytvoříte hash_set; Pokud zadáte žádný objekt delegáta, výchozí hodnota je funkce `System::Object::hash_value(key_type)`. To znamená pro všechny klíče `X` a `Y`:  
  
 `hash_delegate()(X)`vrátí stejný výsledek celé číslo při každém volání.  
  
 Pokud `X` a `Y` mít ekvivalentní řazení, pak `hash_delegate()(X)` by měla vrátit stejný výsledek celé číslo jako `hash_delegate()(Y)`.  
  
 Každý prvek obsahuje samostatné klíč a hodnotu namapované. Pořadí je reprezentována způsobem, který umožňuje vyhledávání, vkládání a odebírání libovolný element s několik operací, která je nezávislá počet elementů v pořadí (konstantní čas)--alespoň v nejvhodnější případů. Vkládání prvků navíc nezruší platnost žádných iterátorů a odstranění prvku zruší platnost pouze těch iterátorů, které odkazují na odstraněný prvek.  
  
 V případě hodnoty hash nejsou distribuovány jednotně, ale můžete degenerovanou tabulku hash. V extreme – funkce hash, který vždy vrací stejnou hodnotu – vyhledávání, vkládání a odebrání jsou úměrná počet elementů v pořadí (lineární čas). Kontejner endeavors zvolit funkce přiměřenou hodnotu hash, střední sady velikost a velikost zatřiďovací tabulku (celkový počet kbelíků), ale můžete přepsat některé nebo všechny tyto volby. Zobrazit, například funkce [hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md) a [hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md).  
  
 Hash_map podporuje obousměrné iterátory, což znamená, že můžete tak, aby přiléhající elementy zadané iterátor, který označuje elementu v řízené sekvenci. Speciální hlavního uzlu odpovídá iterator vrácený [hash_map::end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)`()`. Tato iterator k dosažení poslední elementu v řízené sekvenci, můžete snížení, pokud je k dispozici. Hash_map – iterator k dosažení hlavního uzlu můžete zvýšit a bude potom porovnejte rovna `end()`. Ale nemůže dereference iterator vrácený `end()`.  
  
 Všimněte si, že nemůže odkazovat na prvek hash_map přímo zadané pořadí umístění – vyžadující iterator náhodný přístup.  
  
 Hash_map – iterator uloží popisovač pro jeho přidružené hash_map uzlu, který pak uloží popisovač do jeho přidružené kontejneru. Iterátory lze použít pouze jejich přidružené kontejnerové objekty. Hash_map – iterator zůstane platný tak dlouho, dokud je přidružen některé hash_map její přidružené hash_map uzel. Kromě toho je platný iterator dereferencable – slouží k přístupu k nebo alter hodnota elementu se označí – tak dlouho, dokud není rovno `end()`.  
  
 Mazání nebo odebrání element volání destruktoru pro jeho uložené hodnoty. Zničení kontejneru vymaže všechny elementy. Proto kontejner, jehož typ elementu je třída ref zajistí, že žádné elementy outlive kontejneru. Upozorňujeme však, že nemá kontejner popisovače `not` zrušení jeho elementy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / hash_map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_map –](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [Sada (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Referenční příručka knihovny STL/CLR](../dotnet/stl-clr-library-reference.md)