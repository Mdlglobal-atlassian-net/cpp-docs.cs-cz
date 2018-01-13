---
title: "Třída CRBTree | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRBTree
- ATLCOLL/ATL::CRBTree
- ATLCOLL/ATL::CRBTree::KINARGTYPE
- ATLCOLL/ATL::CRBTree::KOUTARGTYPE
- ATLCOLL/ATL::CRBTree::VINARGTYPE
- ATLCOLL/ATL::CRBTree::VOUTARGTYPE
- ATLCOLL/ATL::CRBTree::FindFirstKeyAfter
- ATLCOLL/ATL::CRBTree::GetAt
- ATLCOLL/ATL::CRBTree::GetCount
- ATLCOLL/ATL::CRBTree::GetHeadPosition
- ATLCOLL/ATL::CRBTree::GetKeyAt
- ATLCOLL/ATL::CRBTree::GetNext
- ATLCOLL/ATL::CRBTree::GetNextAssoc
- ATLCOLL/ATL::CRBTree::GetNextKey
- ATLCOLL/ATL::CRBTree::GetNextValue
- ATLCOLL/ATL::CRBTree::GetPrev
- ATLCOLL/ATL::CRBTree::GetTailPosition
- ATLCOLL/ATL::CRBTree::GetValueAt
- ATLCOLL/ATL::CRBTree::IsEmpty
- ATLCOLL/ATL::CRBTree::RemoveAll
- ATLCOLL/ATL::CRBTree::RemoveAt
- ATLCOLL/ATL::CRBTree::SetValueAt
dev_langs: C++
helpviewer_keywords: CRBTree class
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f436a3661f027ba1026a60982cb18b48a2c48cc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crbtree-class"></a>CRBTree – třída
Tato třída poskytuje metody pro vytvoření a použití Red černé stromu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename K,
          typename V, 
          class KTraits = CElementTraits<K>, 
          class VTraits = CElementTraits<V>> 
class CRBTree
```  
  
#### <a name="parameters"></a>Parametry  
 `K`  
 Typ klíče elementu.  
  
 *V*  
 Typ elementu hodnotu.  
  
 `KTraits`  
 Kód používaný k zkopírovat nebo přesunout klíčové prvky. V tématu [CElementTraits třída](../../atl/reference/celementtraits-class.md) další podrobnosti.  
  
 `VTraits`  
 Kód používaný k zkopírovat nebo přesunout hodnotu elementy.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CRBTree::KINARGTYPE](#kinargtype)|Typ použitý při klíč se předá jako vstupní argument.|  
|[CRBTree::KOUTARGTYPE](#koutargtype)|Typ použitý při klíč se vrátí jako argument výstup.|  
|[CRBTree::VINARGTYPE](#vinargtype)|Typ použitý při hodnotu se předá jako vstupní argument.|  
|[CRBTree::VOUTARGTYPE](#voutargtype)|Typ použitý při hodnotu je předat jako argument výstup.|  
  
### <a name="public-classes"></a>Veřejné třídy  
  
|Název|Popis|  
|----------|-----------------|  
|[CRBTree::CPair – třída](#cpair_class)|Třída obsahující prvky klíč a hodnotu.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CRBTree:: ~ CRBTree](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)|Voláním této metody lze najít pozici elementu, který používá další klíč k dispozici.|  
|[CRBTree::GetAt](#getat)|Volejte tuto metodu za účelem získání elementu na dané pozici ve stromové struktuře.|  
|[CRBTree::GetCount](#getcount)|Volejte tuto metodu za účelem získání počet elementů ve stromové struktuře.|  
|[CRBTree::GetHeadPosition](#getheadposition)|Volejte tuto metodu k získání hodnoty pozice pro element v head stromu.|  
|[CRBTree::GetKeyAt](#getkeyat)|Volejte tuto metodu za účelem získání klíče z dané pozici ve stromové struktuře.|  
|[CRBTree::GetNext](#getnext)|Volat tuto metodu za účelem získání ukazatele na element uložené v `CRBTree` objektu a přechodu na další prvek pozici.|  
|[CRBTree::GetNextAssoc](#getnextassoc)|Volat tuto metodu za účelem získání klíče a hodnoty elementu uložené v mapě a přechodu na další prvek pozici.|  
|[CRBTree::GetNextKey](#getnextkey)|Volat tuto metodu za účelem získání klíče elementu uložené ve stromové struktuře a přechodu na další prvek pozici.|  
|[CRBTree::GetNextValue](#getnextvalue)|Volat tuto metodu k získání hodnoty elementu uložené ve stromové struktuře a přechodu na další prvek pozici.|  
|[CRBTree::GetPrev](#getprev)|Volat tuto metodu za účelem získání ukazatele na element uložené v `CRBTree` objektu a pak aktualizujte pozici na předchozí element.|  
|[CRBTree::GetTailPosition](#gettailposition)|Volejte tuto metodu k získání hodnoty pozice pro prvek na konec stromu.|  
|[CRBTree::GetValueAt](#getvalueat)|Volat tuto metodu za účelem načtení s hodnotou uloženou na dané pozici v `CRBTree` objektu.|  
|[CRBTree::IsEmpty](#isempty)|Volejte tuto metodu za účelem testování pro objekt stromu prázdná.|  
|[CRBTree::RemoveAll](#removeall)|Voláním této metody lze odebrat všechny elementy z **CRBTree** objektu.|  
|[CRBTree::RemoveAt](#removeat)|Voláním této metody lze odebrat – element na dané pozici v **CRBTree** objektu.|  
|[CRBTree::SetValueAt](#setvalueat)|Voláním této metody lze změnit hodnotu uloženou na dané pozici v `CRBTree` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Red černé stromu je binární vyhledávání stromové struktury, která používá navíc bit informací na uzel zajistit, aby zůstal "vyrovnáváním,", je, není height stromu růst nepřiměřeně velké a mají vliv na výkon.  
  
 Tato třída šablony je určen k použití podle [CRBMap](../../atl/reference/crbmap-class.md) a [CRBMultiMap](../../atl/reference/crbmultimap-class.md). Hromadné metod, které tvoří tyto odvozené třídy jsou poskytovány `CRBTree`.  
  
 Podrobnější informace o různých třídy kolekce a jejich funkce a vlastnosti výkonu, najdete v části [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="cpair_class"></a>CRBTree::CPair – třída  
 Třída obsahující prvky klíč a hodnotu.  
  
```
class CPair : public __POSITION
```  
  
### <a name="remarks"></a>Poznámky  
 Tato třída se používá metodami [CRBTree::GetAt](#getat), [CRBTree::GetNext](#getnext), a [CRBTree::GetPrev](#getprev) pro přístup k klíč a hodnotu elementy, které jsou uložené ve stromové struktuře.  
  
 Členy jsou následující:  
  
|||  
|-|-|  
|`m_key`|Datový člen ukládání klíče elementu.|  
|`m_value`|Datový člen ukládání prvku hodnoty.|  
  
##  <a name="dtor"></a>CRBTree:: ~ CRBTree  
 Destruktor.  
  
```
~CRBTree() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky. Volání [CRBTree::RemoveAll](#removeall) odstranit všechny elementy.  
  
##  <a name="findfirstkeyafter"></a>CRBTree::FindFirstKeyAfter  
 Voláním této metody lze najít pozici elementu, který používá další klíč k dispozici.  
  
```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Hodnotu klíče.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu pozice elementu, který používá další klíč k dispozici. Pokud neexistují žádné další elementy, vrátí se hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda usnadňuje procházení stromu bez nutnosti k výpočtu hodnoty pozice předem.  
  
##  <a name="getat"></a>CRBTree::GetAt  
 Volejte tuto metodu za účelem získání elementu na dané pozici ve stromové struktuře.  
  
```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Hodnota pozice.  
  
 `key`  
 Proměnná, která přijímá klíč.  
  
 *value*  
 Proměnná, která přijímá hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí první dva formuláře ukazatel [CPair](#cpair_class). Třetí formuláře získá klíč a hodnotu pro dané pozici.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota pozice se dá dříve určit pomocí volání metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::GetTailPosition](#gettailposition).  
  
 V sestavení pro ladění k chybě assertion dojde v případě `pos` rovná hodnotu NULL.  
  
##  <a name="getcount"></a>CRBTree::GetCount  
 Volejte tuto metodu za účelem získání počet elementů ve stromové struktuře.  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet elementů (každý pár klíč/hodnota je jeden element) uložené ve stromové struktuře.  
  
##  <a name="getheadposition"></a>CRBTree::GetHeadPosition  
 Volejte tuto metodu k získání hodnoty pozice pro element v head stromu.  
  
```
POSITION GetHeadPosition() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí pozici hodnotu pro element v head stromu.  
  
### <a name="remarks"></a>Poznámky  
 Hodnoty vrácené `GetHeadPosition` lze použít s metodami, jako [CRBTree::GetKeyAt](#getkeyat) nebo [CRBTree::GetNext](#getnext) procházení stromu a k získávání hodnot.  
  
##  <a name="getkeyat"></a>CRBTree::GetKeyAt  
 Volejte tuto metodu za účelem získání klíče z dané pozici ve stromové struktuře.  
  
```
const K& GetKeyAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Hodnota pozice.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí klíč uložený na pozici `pos` ve stromové struktuře.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `pos` není platný pozice hodnota, výsledky mohou být nepředvídatelné. V sestavení pro ladění k chybě assertion dojde v případě `pos` rovná hodnotu NULL.  
  
##  <a name="getnext"></a>CRBTree::GetNext  
 Volat tuto metodu za účelem získání ukazatele na element uložené v `CRBTree` objektu a přechodu na další prvek pozici.  
  
```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Čítač pozice vrácen předchozím voláním metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí ukazatel na další [CPair](#cpair_class) hodnotu ve stromové struktuře.  
  
### <a name="remarks"></a>Poznámky  
 `pos` Pozice počítadlo je aktualizováno po každé volání. Pokud je načtený element poslední ve stromové struktuře `pos` je nastaven na hodnotu NULL.  
  
##  <a name="getnextassoc"></a>CRBTree::GetNextAssoc  
 Volat tuto metodu za účelem získání klíče a hodnoty elementu uložené v mapě a přechodu na další prvek pozici.  
  
```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Čítač pozice vrácen předchozím voláním metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
 `key`  
 Parametr šablony určující typ klíče stromové struktuře.  
  
 *value*  
 Parametr šablony určující typ hodnoty stromové struktuře.  
  
### <a name="remarks"></a>Poznámky  
 `pos` Pozice počítadlo je aktualizováno po každé volání. Pokud je načtený element poslední ve stromové struktuře `pos` je nastaven na hodnotu NULL.  
  
##  <a name="getnextkey"></a>CRBTree::GetNextKey  
 Volat tuto metodu za účelem získání klíče elementu uložené ve stromové struktuře a přechodu na další prvek pozici.  
  
```
const K& GetNextKey(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Čítač pozice vrácen předchozím voláním metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na další klíč ve stromové struktuře.  
  
### <a name="remarks"></a>Poznámky  
 Čítač aktuální pozici aktualizace `pos`. Pokud nejsou žádné další položky ve stromové struktuře, je pozice čítač nastaven na hodnotu NULL.  
  
##  <a name="getnextvalue"></a>CRBTree::GetNextValue  
 Volat tuto metodu k získání hodnoty elementu uložené ve stromové struktuře a přechodu na další prvek pozici.  
  
```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Čítač pozice vrácen předchozím voláním metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na další hodnotu ve stromové struktuře.  
  
### <a name="remarks"></a>Poznámky  
 Čítač aktuální pozici aktualizace `pos`. Pokud nejsou žádné další položky ve stromové struktuře, je pozice čítač nastaven na hodnotu NULL.  
  
##  <a name="getprev"></a>CRBTree::GetPrev  
 Volat tuto metodu za účelem získání ukazatele na element uložené v `CRBTree` objektu a pak aktualizujte pozici na předchozí element.  
  
```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Čítač pozice vrácen předchozím voláním metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na předchozí [CPair](#cpair_class) hodnotou uloženou ve stromové struktuře.  
  
### <a name="remarks"></a>Poznámky  
 Čítač aktuální pozici aktualizace `pos`. Pokud nejsou žádné další položky ve stromové struktuře, je pozice čítač nastaven na hodnotu NULL.  
  
##  <a name="gettailposition"></a>CRBTree::GetTailPosition  
 Volejte tuto metodu k získání hodnoty pozice pro prvek na konec stromu.  
  
```
POSITION GetTailPosition() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu pozici pro prvek na konec stromu.  
  
### <a name="remarks"></a>Poznámky  
 Hodnoty vrácené `GetTailPosition` lze použít s metodami, jako [CRBTree::GetKeyAt](#getkeyat) nebo [CRBTree::GetPrev](#getprev) procházení stromu a k získávání hodnot.  
  
##  <a name="getvalueat"></a>CRBTree::GetValueAt  
 Volat tuto metodu za účelem načtení s hodnotou uloženou na dané pozici v `CRBTree` objektu.  
  
```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Čítač pozice vrácen předchozím voláním metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na s hodnotou uloženou na dané pozici v `CRBTree` objektu.  
  
##  <a name="isempty"></a>CRBTree::IsEmpty  
 Volejte tuto metodu za účelem testování pro objekt stromu prázdná.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** Pokud stromu prázdná, **false** jinak.  
  
##  <a name="kinargtype"></a>CRBTree::KINARGTYPE  
 Typ použitý při klíč se předá jako vstupní argument.  
  
```
typedef KTraits::INARGTYPE KINARGTYPE;
```  
  
##  <a name="koutargtype"></a>CRBTree::KOUTARGTYPE  
 Typ použitý při klíč se vrátí jako argument výstup.  
  
```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```  
  
##  <a name="removeall"></a>CRBTree::RemoveAll  
 Voláním této metody lze odebrat všechny elementy z `CRBTree` objektu.  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vymaže `CRBTree` objekt, uvolnění paměti používá k ukládání elementy.  
  
##  <a name="removeat"></a>CRBTree::RemoveAt  
 Voláním této metody lze odebrat – element na dané pozici v **CRBTree** objektu.  
  
```
void RemoveAt(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Čítač pozice vrácen předchozím voláním metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="remarks"></a>Poznámky  
 Odebere dvojice klíč/hodnota, které jsou uložené na zadané pozici. Je uvolnit paměť, používá k ukládání elementu. POZICE odkazuje `pos` stává neplatným a při pozice všech elementů ve stromové struktuře zůstane platná, nemusí nutně jít udělají zachovat stejné pořadí.  
  
##  <a name="setvalueat"></a>CRBTree::SetValueAt  
 Voláním této metody lze změnit hodnotu uloženou na dané pozici v `CRBTree` objektu.  
  
```
void SetValueAt(POSITION pos, VINARGTYPE value);
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Čítač pozice vrácen předchozím voláním metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
 *value*  
 Hodnota k přidání do `CRBTree` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Změní hodnotu elementu uložené na dané pozici v `CRBTree` objektu.  
  
##  <a name="vinargtype"></a>CRBTree::VINARGTYPE  
 Typ použitý při hodnotu se předá jako vstupní argument.  
  
```
typedef VTraits::INARGTYPE VINARGTYPE;
```  
  
##  <a name="voutargtype"></a>CRBTree::VOUTARGTYPE  
 Typ použitý při hodnotu je předat jako argument výstup.  
  
```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
