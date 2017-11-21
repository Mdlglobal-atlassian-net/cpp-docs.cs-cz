---
title: hash_multimap (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_multimap
dev_langs: C++
helpviewer_keywords:
- hash_multimap class [STL/CLR]
- <cliext/hash_map> header [STL/CLR]
- <hash_map> header [STL/CLR]
ms.assetid: cd78687b-8a05-48e0-9d22-8b8194ae3b0b
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd7b35758caaf76904eb3144d22d747c22f02804
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="hashmultimap-stlclr"></a>hash_multimap (STL/CLR)
Šablony třídy popisuje objekt, který řídí různých délka pořadí elementů, která má obousměrný přístup. Použít metodu kontejneru `hash_multimap` ke správě pořadí elementů jako zatřiďovací tabulku, každý záznam tabulky, ukládání obousměrné propojené seznam uzlů a každý uzel ukládání jeden element. Element obsahuje klíč, pro řazení sekvenci a namapované hodnotu, kterou má význam pro pravé.  
  
 V popisu níže `GValue` je stejný jako:  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 kde:  
  
 `GKey`je stejný jako `Key` Pokud k tomu je typu ref, v takovém případě je`Key^`  
  
 `GMapped`je stejný jako `Mapped` Pokud k tomu je typu ref, v takovém případě je`Mapped^`  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class hash_multimap  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
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
|[hash_multimap::const_iterator (STL/CLR)](../dotnet/hash-multimap-const-iterator-stl-clr.md)|Typ konstantního iterátoru řízené sekvence|  
|[hash_multimap::const_reference (STL/CLR)](../dotnet/hash-multimap-const-reference-stl-clr.md)|Typ konstantního odkazu na prvek|  
|[hash_multimap::const_reverse_iterator (STL/CLR)](../dotnet/hash-multimap-const-reverse-iterator-stl-clr.md)|Typ konstantní zpětné iterator pro řízené sekvenci.|  
|[hash_multimap::difference_type (STL/CLR)](../dotnet/hash-multimap-difference-type-stl-clr.md)|Typ (může být podepsaná) vzdálenost mezi dvěma prvky.|  
|[hash_multimap::generic_container (STL/CLR)](../dotnet/hash-multimap-generic-container-stl-clr.md)|Typ generické rozhraní pro kontejner.|  
|[hash_multimap::generic_iterator (STL/CLR)](../dotnet/hash-multimap-generic-iterator-stl-clr.md)|Typ iterace pro obecné rozhraní kontejneru.|  
|[hash_multimap::generic_reverse_iterator (STL/CLR)](../dotnet/hash-multimap-generic-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro obecné rozhraní kontejneru.|  
|[hash_multimap::generic_value (STL/CLR)](../dotnet/hash-multimap-generic-value-stl-clr.md)|Typ elementu pro obecné rozhraní kontejneru.|  
|[hash_multimap::hasher (STL/CLR)](../dotnet/hash-multimap-hasher-stl-clr.md)|Hash delegáta pro klíč.|  
|[hash_multimap::iterator (STL/CLR)](../dotnet/hash-multimap-iterator-stl-clr.md)|Typ iterátoru řízené sekvence|  
|[hash_multimap::key_compare (STL/CLR)](../dotnet/hash-multimap-key-compare-stl-clr.md)|Řazení delegáta pro dva klíče.|  
|[hash_multimap::key_type (STL/CLR)](../dotnet/hash-multimap-key-type-stl-clr.md)|Typ klíče řazení|  
|[hash_multimap::mapped_type (STL/CLR)](../dotnet/hash-multimap-mapped-type-stl-clr.md)|Typ namapované hodnotu přidruženou každý klíč.|  
|[hash_multimap::Reference (STL/CLR)](../dotnet/hash-multimap-reference-stl-clr.md)|Typ odkazu na prvek|  
|[hash_multimap::reverse_iterator (STL/CLR)](../dotnet/hash-multimap-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro řízené sekvenci.|  
|[hash_multimap::size_type (STL/CLR)](../dotnet/hash-multimap-size-type-stl-clr.md)|Typ (nezáporné) vzdálenost mezi dvěma prvky.|  
|[hash_multimap::value_compare (STL/CLR)](../dotnet/hash-multimap-value-compare-stl-clr.md)|Řazení delegáta pro dvě hodnoty elementu.|  
|[hash_multimap::value_type (STL/CLR)](../dotnet/hash-multimap-value-type-stl-clr.md)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[hash_multimap::begin (STL/CLR)](../dotnet/hash-multimap-begin-stl-clr.md)|Určuje začátek řízené sekvence.|  
|[hash_multimap::bucket_count (STL/CLR)](../dotnet/hash-multimap-bucket-count-stl-clr.md)|Spočítá počet intervalů.|  
|[hash_multimap::clear (STL/CLR)](../dotnet/hash-multimap-clear-stl-clr.md)|Odebere všechny prvky.|  
|[hash_multimap::Count (STL/CLR)](../dotnet/hash-multimap-count-stl-clr.md)|Vrátí počet prvků odpovídající zadaného klíče.|  
|[hash_multimap::Empty (STL/CLR)](../dotnet/hash-multimap-empty-stl-clr.md)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[hash_multimap::end (STL/CLR)](../dotnet/hash-multimap-end-stl-clr.md)|Určuje konec řízené sekvence.|  
|[hash_multimap::equal_range (STL/CLR)](../dotnet/hash-multimap-equal-range-stl-clr.md)|Najde rozsah, který odpovídá zadanému klíči.|  
|[hash_multimap::Erase (STL/CLR)](../dotnet/hash-multimap-erase-stl-clr.md)|Odebere prvky v určených pozicích.|  
|[hash_multimap::Find (STL/CLR)](../dotnet/hash-multimap-find-stl-clr.md)|Vyhledá prvek, který odpovídá zadanému klíči.|  
|[hash_multimap::hash_delegate (STL/CLR)](../dotnet/hash-multimap-hash-delegate-stl-clr.md)|Zkopíruje hash delegáta pro klíč.|  
|[hash_multimap::hash_multimap (STL/CLR)](../dotnet/hash-multimap-hash-multimap-stl-clr.md)|Sestaví objekt kontejneru.|  
|[hash_multimap::Insert (STL/CLR)](../dotnet/hash-multimap-insert-stl-clr.md)|Přidá prvky.|  
|[hash_multimap::key_comp (STL/CLR)](../dotnet/hash-multimap-key-comp-stl-clr.md)|Zkopíruje řazení delegáta pro dva klíče.|  
|[hash_multimap::load_factor (STL/CLR)](../dotnet/hash-multimap-load-factor-stl-clr.md)|Spočítá průměrný počet prvků na kbelík.|  
|[hash_multimap::lower_bound (STL/CLR)](../dotnet/hash-multimap-lower-bound-stl-clr.md)|Najde začátek rozsahu, který odpovídá zadaným klíčem.|  
|[hash_multimap::make_value (STL/CLR)](../dotnet/hash-multimap-make-value-stl-clr.md)|Vytvoří objekt hodnoty.|  
|[hash_multimap::max_load_factor (STL/CLR)](../dotnet/hash-multimap-max-load-factor-stl-clr.md)|Získá nebo nastaví maximální počet prvků na kbelík.|  
|[hash_multimap::rbegin (STL/CLR)](../dotnet/hash-multimap-rbegin-stl-clr.md)|Označuje začátek odstínech řízené sekvenci.|  
|[hash_multimap::rehash (STL/CLR)](../dotnet/hash-multimap-rehash-stl-clr.md)|Znovu vytvoří hashovací tabulku.|  
|[hash_multimap::rend (STL/CLR)](../dotnet/hash-multimap-rend-stl-clr.md)|Označuje konec odstínech řízené sekvenci.|  
|[hash_multimap::size (STL/CLR)](../dotnet/hash-multimap-size-stl-clr.md)|Spočítá počet prvků.|  
|[hash_multimap::swap (STL/CLR)](../dotnet/hash-multimap-swap-stl-clr.md)|Zamění obsah dvou kontejnerů.|  
|[hash_multimap::to_array (STL/CLR)](../dotnet/hash-multimap-to-array-stl-clr.md)|Zkopíruje řízené sekvenci do nové pole.|  
|[hash_multimap::upper_bound (STL/CLR)](../dotnet/hash-multimap-upper-bound-stl-clr.md)|Najde konec rozsahu, který odpovídá zadaným klíčem.|  
|[hash_multimap::value_comp (STL/CLR)](../dotnet/hash-multimap-value-comp-stl-clr.md)|Zkopíruje řazení delegáta pro dvě hodnoty elementu.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[hash_multimap::Operator = (STL/CLR)](../dotnet/hash-multimap-operator-assign-stl-clr.md)|Nahradí řízené sekvenci.|  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|<xref:System.ICloneable>|Duplicitní objekt.|  
|<xref:System.Collections.IEnumerable>|Pořadí pomocí elementů.|  
|<xref:System.Collections.ICollection>|Údržba skupiny elementů.|  
|<xref:System.Collections.Generic.IEnumerable%601>|Pořadí prostřednictvím typové elementy.|  
|<xref:System.Collections.Generic.ICollection%601>|Údržba skupiny typové elementů.|  
|IHash\<klíče, hodnota >|Udržujte obecné kontejneru.|  
  
## <a name="remarks"></a>Poznámky  
 Objekt přiděluje a uvolní úložiště pro pořadí, které ovládá jako jednotlivé uzly v obousměrných odkazovaného seznamu. Objekt k urychlení přístupu, také udržuje různých délka pole ukazatele do seznamu (zatřiďovací tabulku), efektivně spravovat celý seznam jako posloupnost podřízených seznamů, nebo intervalů. Vloží elementy na bloku, který udržuje seřazené změnou propojení mezi uzly, nikdy zkopírováním obsah jednoho uzlu do jiného. To znamená, že můžete vložit a odeberte elementy volně bez narušení zbývající elementy.  
  
 Objekt řadí každé sady jimi řídí voláním objektu uložené delegáta typu [hash_set::key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md). Objekt uložené delegáta můžete zadat, když vytvoříte hash_set; Pokud zadáte žádný objekt delegáta, výchozí hodnota je porovnání `operator<=(key_type, key_type)`.  
  
 Přístup k objektu uložené delegáta voláním členské funkce [hash_set::key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)`()`. Takový objekt delegáta musí definovat ekvivalentní řazení mezi klíče typu [hash_set::key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md). To znamená, pro žádné dva klíče `X` a `Y`:  
  
 `key_comp()(X, Y)`Vrátí stejné logická hodnota způsobit při každém volání.  
  
 Pokud `key_comp()(X, Y) && key_comp()(Y, X)` má hodnotu true, pak `X` a `Y` se říká, že máte ekvivalentní řazení.  
  
 Jakékoli řazení pravidlo, které se chovají jako `operator<=(key_type, key_type)`, `operator>=(key_type, key_type)` nebo `operator==(key_type, key_type)` definuje eqivalent řazení.  
  
 Všimněte si, že kontejner je zajištěná pouze elementy jejichž klíče měly ekvivalentní řazení (a které hash na stejnou hodnotu celé číslo) sousedících v sadě. Na rozdíl od třídy šablony [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md), objekt třídy šablony `hash_multimap` nevyžaduje, aby klíče pro všechny elementy byly jedinečné. (Dvě nebo více klíčů může mít ekvivalentní řazení.)  
  
 Určuje objekt sady, které by měl obsahovat k danému klíči řazení při volání objektu uložené delegáta typu [hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md). Přístup k této uložené objekt voláním členské funkce [hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) `()` získat celočíselná hodnota, která závisí na hodnotu klíče. Objekt uložené delegáta můžete zadat, když vytvoříte hash_set; Pokud zadáte žádný objekt delegáta, výchozí hodnota je funkce `System::Object::hash_value(key_type)`. To znamená pro všechny klíče `X` a `Y`:  
  
 `hash_delegate()(X)`vrátí stejný výsledek celé číslo při každém volání.  
  
 Pokud `X` a `Y` mít ekvivalentní řazení, pak `hash_delegate()(X)` by měla vrátit stejný výsledek celé číslo jako `hash_delegate()(Y)`.  
  
 Každý prvek obsahuje samostatné klíč a hodnotu namapované. Pořadí je reprezentována způsobem, který umožňuje vyhledávání, vkládání a odebírání libovolný element s několik operací, která je nezávislá počet elementů v pořadí (konstantní čas)--alespoň v nejvhodnější případů. Vkládání prvků navíc nezruší platnost žádných iterátorů a odstranění prvku zruší platnost pouze těch iterátorů, které odkazují na odstraněný prvek.  
  
 V případě hodnoty hash nejsou distribuovány jednotně, ale můžete degenerovanou tabulku hash. V extreme – funkce hash, který vždy vrací stejnou hodnotu – vyhledávání, vkládání a odebrání jsou úměrná počet elementů v pořadí (lineární čas). Kontejner endeavors zvolit funkce přiměřenou hodnotu hash, střední sady velikost a velikost zatřiďovací tabulku (celkový počet kbelíků), ale můžete přepsat některé nebo všechny tyto volby. Zobrazit, například funkce [hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md) a [hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md).  
  
 Hash_multimap podporuje obousměrné iterátory, což znamená, že můžete tak, aby přiléhající elementy zadané iterátor, který označuje elementu v řízené sekvenci. Speciální hlavního uzlu odpovídá iterator vrácený [hash_multimap::end (STL/CLR)](../dotnet/hash-multimap-end-stl-clr.md)`()`. Tato iterator k dosažení poslední elementu v řízené sekvenci, můžete snížení, pokud je k dispozici. Můžete zvýšit iterator hash_multimap k dosažení hlavního uzlu a pak se porovná rovna `end()`. Ale nemůže dereference iterator vrácený `end()`.  
  
 Všimněte si, že nemůže odkazovat na prvek hash_multimap přímo zadané pořadí umístění – vyžadující iterator náhodný přístup.  
  
 Hash_multimap iterator uloží popisovač do přidružené hash_multimap uzlu, který je pak uloží popisovač pro jeho přidružené kontejneru. Iterátory lze použít pouze jejich přidružené kontejnerové objekty. Hash_multimap iterator zůstane platný tak dlouho, dokud je přidružen některé hash_multimap její přidružené hash_multimap uzel. Kromě toho je platný iterator dereferencable – slouží k přístupu k nebo alter hodnota elementu se označí – tak dlouho, dokud není rovno `end()`.  
  
 Mazání nebo odebrání element volání destruktoru pro jeho uložené hodnoty. Zničení kontejneru vymaže všechny elementy. Proto kontejner, jehož typ elementu je třída ref zajistí, že žádné elementy outlive kontejneru. Upozorňujeme však, že nemá kontejner popisovače `not` zrušení jeho elementy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / hash_map >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_map – (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [Sada (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Referenční příručka knihovny STL/CLR](../dotnet/stl-clr-library-reference.md)