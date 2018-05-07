---
title: hash_set (STL/CLR) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_set
dev_langs:
- C++
helpviewer_keywords:
- <cliext/hash_set> header [STL/CLR]
- hash_set class [STL/CLR]
- <hash_set> header [STL/CLR]
ms.assetid: d110e356-ba3e-4e52-9e2d-d997bf975c96
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 63b43a116848ff67deb9c62c04849aa5afc6dbc1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="hashset-stlclr"></a>hash_set (STL/CLR)
Šablony třídy popisuje objekt, který řídí různých délka pořadí elementů, která má obousměrný přístup. Použít metodu kontejneru `hash_set` ke správě pořadí elementů jako zatřiďovací tabulku, každý záznam tabulky, ukládání obousměrné propojené seznam uzlů a každý uzel ukládání jeden element. Hodnota jednotlivých prvků slouží jako klíč k pořadí řazení.  
  
 V popisu níže `GValue` je stejný jako `GKey`, který naopak je stejný jako `Key` Pokud k tomu je typu ref, v takovém případě je `Key^`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename Key>  
    ref class hash_set  
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
  
## <a name="members"></a>Členové  
  
|Definice typu|Popis|  
|---------------------|-----------------|  
|[hash_set::const_iterator (STL/CLR)](../dotnet/hash-set-const-iterator-stl-clr.md)|Typ konstantního iterátoru řízené sekvence|  
|[hash_set::const_reference (STL/CLR)](../dotnet/hash-set-const-reference-stl-clr.md)|Typ konstantního odkazu na prvek|  
|[hash_set::const_reverse_iterator (STL/CLR)](../dotnet/hash-set-const-reverse-iterator-stl-clr.md)|Typ konstantní zpětné iterator pro řízené sekvenci.|  
|[hash_set::difference_type (STL/CLR)](../dotnet/hash-set-difference-type-stl-clr.md)|Typ (může být podepsaná) vzdálenost mezi dvěma prvky.|  
|[hash_set::generic_container (STL/CLR)](../dotnet/hash-set-generic-container-stl-clr.md)|Typ generické rozhraní pro kontejner.|  
|[hash_set::generic_iterator (STL/CLR)](../dotnet/hash-set-generic-iterator-stl-clr.md)|Typ iterace pro obecné rozhraní kontejneru.|  
|[hash_set::generic_reverse_iterator (STL/CLR)](../dotnet/hash-set-generic-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro obecné rozhraní kontejneru.|  
|[hash_set::generic_value (STL/CLR)](../dotnet/hash-set-generic-value-stl-clr.md)|Typ elementu pro obecné rozhraní kontejneru.|  
|[hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md)|Hash delegáta pro klíč.|  
|[hash_set::iterator (STL/CLR)](../dotnet/hash-set-iterator-stl-clr.md)|Typ iterátoru řízené sekvence|  
|[hash_set::key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md)|Řazení delegáta pro dva klíče.|  
|[hash_set::key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md)|Typ klíče řazení|  
|[hash_set::reference (STL/CLR)](../dotnet/hash-set-reference-stl-clr.md)|Typ odkazu na prvek|  
|[hash_set::reverse_iterator (STL/CLR)](../dotnet/hash-set-reverse-iterator-stl-clr.md)|Typ zpětné iterator pro řízené sekvenci.|  
|[hash_set::size_type (STL/CLR)](../dotnet/hash-set-size-type-stl-clr.md)|Typ (nezáporné) vzdálenost mezi dvěma prvky.|  
|[hash_set::value_compare (STL/CLR)](../dotnet/hash-set-value-compare-stl-clr.md)|Řazení delegáta pro dvě hodnoty elementu.|  
|[hash_set::value_type (STL/CLR)](../dotnet/hash-set-value-type-stl-clr.md)|Typ prvku|  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[hash_set::begin (STL/CLR)](../dotnet/hash-set-begin-stl-clr.md)|Určuje začátek řízené sekvence.|  
|[hash_set::bucket_count (STL/CLR)](../dotnet/hash-set-bucket-count-stl-clr.md)|Spočítá počet intervalů.|  
|[hash_set::clear (STL/CLR)](../dotnet/hash-set-clear-stl-clr.md)|Odebere všechny prvky.|  
|[hash_set::count (STL/CLR)](../dotnet/hash-set-count-stl-clr.md)|Vrátí počet prvků odpovídající zadaného klíče.|  
|[hash_set::empty (STL/CLR)](../dotnet/hash-set-empty-stl-clr.md)|Zkouší, zda nejsou přítomny žádné prvky.|  
|[hash_set::end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)|Určuje konec řízené sekvence.|  
|[hash_set::equal_range (STL/CLR)](../dotnet/hash-set-equal-range-stl-clr.md)|Najde rozsah, který odpovídá zadanému klíči.|  
|[hash_set::erase (STL/CLR)](../dotnet/hash-set-erase-stl-clr.md)|Odebere prvky v určených pozicích.|  
|[hash_set::find (STL/CLR)](../dotnet/hash-set-find-stl-clr.md)|Vyhledá prvek, který odpovídá zadanému klíči.|  
|[hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md)|Zkopíruje hash delegáta pro klíč.|  
|[hash_set::hash_set (STL/CLR)](../dotnet/hash-set-hash-set-stl-clr.md)|Sestaví objekt kontejneru.|  
|[hash_set::insert (STL/CLR)](../dotnet/hash-set-insert-stl-clr.md)|Přidá prvky.|  
|[hash_set::key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)|Zkopíruje řazení delegáta pro dva klíče.|  
|[hash_set::load_factor (STL/CLR)](../dotnet/hash-set-load-factor-stl-clr.md)|Spočítá průměrný počet prvků na kbelík.|  
|[hash_set::lower_bound (STL/CLR)](../dotnet/hash-set-lower-bound-stl-clr.md)|Najde začátek rozsahu, který odpovídá zadaným klíčem.|  
|[hash_set::make_value (STL/CLR)](../dotnet/hash-set-make-value-stl-clr.md)|Vytvoří objekt hodnoty.|  
|[hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md)|Získá nebo nastaví maximální počet prvků na kbelík.|  
|[hash_set::rbegin (STL/CLR)](../dotnet/hash-set-rbegin-stl-clr.md)|Označuje začátek odstínech řízené sekvenci.|  
|[hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md)|Znovu vytvoří hashovací tabulku.|  
|[hash_set::rend (STL/CLR)](../dotnet/hash-set-rend-stl-clr.md)|Označuje konec odstínech řízené sekvenci.|  
|[hash_set::size (STL/CLR)](../dotnet/hash-set-size-stl-clr.md)|Spočítá počet prvků.|  
|[hash_set::swap (STL/CLR)](../dotnet/hash-set-swap-stl-clr.md)|Zamění obsah dvou kontejnerů.|  
|[hash_set::to_array (STL/CLR)](../dotnet/hash-set-to-array-stl-clr.md)|Zkopíruje řízené sekvenci do nové pole.|  
|[hash_set::upper_bound (STL/CLR)](../dotnet/hash-set-upper-bound-stl-clr.md)|Najde konec rozsahu, který odpovídá zadaným klíčem.|  
|[hash_set::value_comp (STL/CLR)](../dotnet/hash-set-value-comp-stl-clr.md)|Zkopíruje řazení delegáta pro dvě hodnoty elementu.|  
  
|Operátor|Popis|  
|--------------|-----------------|  
|[hash_set::operator= (STL/CLR)](../dotnet/hash-set-operator-assign-stl-clr.md)|Nahradí řízené sekvenci.|  
  
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
  
 `key_comp()(X, Y)` Vrátí stejné logická hodnota způsobit při každém volání.  
  
 Pokud `key_comp()(X, Y) && key_comp()(Y, X)` má hodnotu true, pak `X` a `Y` se říká, že máte ekvivalentní řazení.  
  
 Jakékoli řazení pravidlo, které se chovají jako `operator<=(key_type, key_type)`, `operator>=(key_type, key_type)` nebo `operator==(key_type, key_type)` definuje eqivalent řazení.  
  
 Všimněte si, že kontejner je zajištěná pouze elementy jejichž klíče měly ekvivalentní řazení (a které hash na stejnou hodnotu celé číslo) sousedících v sadě. Na rozdíl od třídy šablony [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md), objekt třídy šablony `hash_set` zajišťuje, aby klíče pro všechny elementy byly jedinečné. (Žádná dva klíče mít ekvivalentní řazení.)  
  
 Určuje objekt sady, které by měl obsahovat k danému klíči řazení při volání objektu uložené delegáta typu [hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md). Přístup k této uložené objekt voláním členské funkce [hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) `()` získat celočíselná hodnota, která závisí na hodnotu klíče. Objekt uložené delegáta můžete zadat, když vytvoříte hash_set; Pokud zadáte žádný objekt delegáta, výchozí hodnota je funkce `System::Object::hash_value(key_type)`. To znamená pro všechny klíče `X` a `Y`:  
  
 `hash_delegate()(X)` vrátí stejný výsledek celé číslo při každém volání.  
  
 Pokud `X` a `Y` mít ekvivalentní řazení, pak `hash_delegate()(X)` by měla vrátit stejný výsledek celé číslo jako `hash_delegate()(Y)`.  
  
 Každý prvek slouží jako klíč a hodnotu. Pořadí je reprezentována způsobem, který umožňuje vyhledávání, vkládání a odebírání libovolný element s několik operací, která je nezávislá počet elementů v pořadí (konstantní čas)--alespoň v nejvhodnější případů. Vkládání prvků navíc nezruší platnost žádných iterátorů a odstranění prvku zruší platnost pouze těch iterátorů, které odkazují na odstraněný prvek.  
  
 V případě hodnoty hash nejsou distribuovány jednotně, ale můžete degenerovanou tabulku hash. V extreme – funkce hash, který vždy vrací stejnou hodnotu – vyhledávání, vkládání a odebrání jsou úměrná počet elementů v pořadí (lineární čas). Kontejner endeavors zvolit funkce přiměřenou hodnotu hash, střední sady velikost a velikost zatřiďovací tabulku (celkový počet kbelíků), ale můžete přepsat některé nebo všechny tyto volby. Zobrazit, například funkce [hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md) a [hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md).  
  
 Hash_set podporuje obousměrné iterátory, což znamená, že můžete tak, aby přiléhající elementy zadané iterátor, který označuje elementu v řízené sekvenci. Speciální hlavního uzlu odpovídá iterator vrácený [hash_set::end (STL/CLR)](../dotnet/hash-set-end-stl-clr.md)`()`. Tato iterator k dosažení poslední elementu v řízené sekvenci, můžete snížení, pokud je k dispozici. Můžete zvýšit iterator hash_set k dosažení hlavního uzlu a pak se porovná rovna `end()`. Ale nemůže dereference iterator vrácený `end()`.  
  
 Všimněte si, že nemůže odkazovat na prvek hash_set přímo zadané pořadí umístění – vyžadující iterator náhodný přístup.  
  
 Hash_set iterator uloží popisovač do přidružené hash_set uzlu, který je pak uloží popisovač pro jeho přidružené kontejneru. Iterátory lze použít pouze jejich přidružené kontejnerové objekty. Hash_set – iterator zůstane platný tak dlouho, dokud je přidružen některé hash_set její přidružené hash_set uzel. Kromě toho je platný iterator dereferencable – slouží k přístupu k nebo alter hodnota elementu se označí – tak dlouho, dokud není rovno `end()`.  
  
 Mazání nebo odebrání element volání destruktoru pro jeho uložené hodnoty. Zničení kontejneru vymaže všechny elementy. Proto kontejner, jehož typ elementu je třída ref zajistí, že žádné elementy outlive kontejneru. Upozorňujeme však, že nemá kontejner popisovače `not` zrušení jeho elementy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / hash_set >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [hash_map – (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_set –](../dotnet/hash-set-stl-clr.md)   
 [hash_set –](../dotnet/hash-set-stl-clr.md)   
 [mapy (STL/CLR)](../dotnet/map-stl-clr.md)   
 [Sada (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Sada (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Sada (STL/CLR)](../dotnet/set-stl-clr.md)   
 [Referenční dokumentace knihoven STL/CLR](../dotnet/stl-clr-library-reference.md)