---
title: Crbtree – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
dev_langs:
- C++
helpviewer_keywords:
- CRBTree class
ms.assetid: a1b1cb63-38e4-4fc2-bb28-f774d1721760
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 10ca0fee1bb88b205732590b085cb9ddfe9a6c10
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885790"
---
# <a name="crbtree-class"></a>Crbtree – třída
Tato třída poskytuje metody pro vytváření a využívání Red černé stromu.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename K,
          typename V, 
          class KTraits = CElementTraits<K>, 
          class VTraits = CElementTraits<V>> 
class CRBTree
```  
  
#### <a name="parameters"></a>Parametry  
 *K*  
 Typ klíče prvku.  
  
 *V*  
 Typ elementu hodnota.  
  
 *KTraits*  
 Kód použitý má zkopírovat nebo přesunout klíčové prvky. Zobrazit [celementtraits – třída](../../atl/reference/celementtraits-class.md) další podrobnosti.  
  
 *VTraits*  
 Kód použitý má zkopírovat nebo přesunout elementy hodnotu.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CRBTree::KINARGTYPE](#kinargtype)|Typ použitý klíč je předána jako vstupní argument.|  
|[CRBTree::KOUTARGTYPE](#koutargtype)|Typ použitý při klíč se vrátí jako výstup argument.|  
|[CRBTree::VINARGTYPE](#vinargtype)|Typ použitý jako vstupní argument je předána hodnota.|  
|[CRBTree::VOUTARGTYPE](#voutargtype)|Typ použitý při je hodnota předána jako argument výstup.|  
  
### <a name="public-classes"></a>Veřejné třídy  
  
|Název|Popis|  
|----------|-----------------|  
|[Třída CRBTree::CPair](#cpair_class)|Třída obsahující prvky klíč a hodnotu.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Crbtree –:: ~ crbtree –](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CRBTree::FindFirstKeyAfter](#findfirstkeyafter)|Volání této metody pro hledání pozice prvku, který se používá k dispozici další klíč.|  
|[CRBTree::GetAt](#getat)|Volejte tuto metodu za účelem získání elementu na dané pozici ve stromu.|  
|[CRBTree::GetCount](#getcount)|Volejte tuto metodu za účelem získání počet prvků ve stromové struktuře.|  
|[CRBTree::GetHeadPosition](#getheadposition)|Volejte tuto metodu za účelem získání hodnoty pozice pro element na hlavu stromu.|  
|[CRBTree::GetKeyAt](#getkeyat)|Volejte tuto metodu za účelem získání klíče z dané pozici ve stromu.|  
|[CRBTree::GetNext](#getnext)|Volejte tuto metodu za účelem získání ukazatele na prvek uložený v `CRBTree` objektu a umístění, přejděte na další prvek.|  
|[CRBTree::GetNextAssoc](#getnextassoc)|Volat tuto metodu za účelem získání klíč a hodnotu prvek uložený v objektu map a pozice, přejděte na další prvek.|  
|[CRBTree::GetNextKey](#getnextkey)|Volejte tuto metodu za účelem získání klíče prvek uložený ve stromové struktuře a umístění, přejděte na další prvek.|  
|[CRBTree::GetNextValue](#getnextvalue)|Volání této metody k získání hodnoty prvek uložený ve stromové struktuře a umístění, přejděte na další prvek.|  
|[CRBTree::GetPrev](#getprev)|Volejte tuto metodu za účelem získání ukazatele na prvek uložený v `CRBTree` objektu a pak aktualizujte umístění na předchozí prvek.|  
|[CRBTree::GetTailPosition](#gettailposition)|Volejte tuto metodu za účelem získání hodnoty pozice pro prvek na konec stromu.|  
|[CRBTree::GetValueAt](#getvalueat)|Volejte tuto metodu za účelem načtení hodnoty uložené na dané pozici v `CRBTree` objektu.|  
|[CRBTree::IsEmpty](#isempty)|Volejte tuto metodu za účelem testování pro objekt prázdný strom.|  
|[CRBTree::RemoveAll](#removeall)|Voláním této metody lze odebrat všechny prvky z `CRBTree` objektu.|  
|[CRBTree::RemoveAt](#removeat)|Volejte tuto metodu za účelem odebrání elementu na dané pozici v `CRBTree` objektu.|  
|[CRBTree::SetValueAt](#setvalueat)|Voláním této metody lze změnit hodnotu uloženou v dané pozici v `CRBTree` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Tree černý Red je binárního vyhledávacího stromu, který používá speciální hodně informací za uzel a zajistěte, aby zůstal "Rovnováha,", který je, výšku stromu nebude zvětšovat nepřiměřeně velké a ovlivnit výkon.  
  
 Tato třída šablony slouží k využívat [crbmap –](../../atl/reference/crbmap-class.md) a [crbmultimap –](../../atl/reference/crbmultimap-class.md). Hromadné metody, které tvoří tyto odvozené třídy jsou k dispozici v `CRBTree`.  
  
 Podrobnější diskuzi o různých třídy kolekcí a jejich funkce a výkonové charakteristiky, naleznete v tématu [ATL – třídy kolekce](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcoll.h  
  
##  <a name="cpair_class"></a>  Třída CRBTree::CPair  
 Třída obsahující prvky klíč a hodnotu.  
  
```
class CPair : public __POSITION
```  
  
### <a name="remarks"></a>Poznámky  
 Tato třída se používá metody [CRBTree::GetAt](#getat), [CRBTree::GetNext](#getnext), a [CRBTree::GetPrev](#getprev) pro přístup k prvkům klíč a hodnotu, uložené ve stromové struktuře.  
  
 Členové jsou následující:  
  
|||  
|-|-|  
|`m_key`|Datový člen ukládání klíčovým prvkem.|  
|`m_value`|Datový člen ukládání prvku hodnoty.|  
  
##  <a name="dtor"></a>  Crbtree –:: ~ crbtree –  
 Destruktor.  
  
```
~CRBTree() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky. Volání [CRBTree::RemoveAll](#removeall) odstranit všechny elementy.  
  
##  <a name="findfirstkeyafter"></a>  CRBTree::FindFirstKeyAfter  
 Volání této metody pro hledání pozice prvku, který se používá k dispozici další klíč.  
  
```
POSITION FindFirstKeyAfter(KINARGTYPE key) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *Klíč*  
 Hodnotu klíče.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu pozice prvku, který se používá k dispozici další klíč. Pokud neexistují žádné další prvky, je vrácena hodnota NULL.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda usnadňuje procházení stromu bez nutnosti k výpočtu hodnoty pozice předem.  
  
##  <a name="getat"></a>  CRBTree::GetAt  
 Volejte tuto metodu za účelem získání elementu na dané pozici ve stromu.  
  
```
CPair* GetAt(POSITION pos) throw();
const CPair* GetAt(POSITION pos) const throw();
void GetAt(POSITION pos, KOUTARGTYPE key, VOUTARGTYPE value) const;
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 Hodnota pozice.  
  
 *Klíč*  
 Proměnná, která přijímá klávesu.  
  
 *value*  
 Proměnné, která přijímá hodnotu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na první dva formuláře [CPair](#cpair_class). Třetí formuláře získá klíč a hodnotu pro danou pozici.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota pozice lze dříve určit pomocí volání metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::GetTailPosition](#gettailposition).  
  
 V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud *pos* je rovna hodnotě NULL.  
  
##  <a name="getcount"></a>  CRBTree::GetCount  
 Volejte tuto metodu za účelem získání počet prvků ve stromové struktuře.  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet prvků (každý pár klíč/hodnota je jeden element) uložené ve stromové struktuře.  
  
##  <a name="getheadposition"></a>  CRBTree::GetHeadPosition  
 Volejte tuto metodu za účelem získání hodnoty pozice pro element na hlavu stromu.  
  
```
POSITION GetHeadPosition() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu pozice pro element na hlavu stromu.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vrácená `GetHeadPosition` lze použít s metodami, jako [CRBTree::GetKeyAt](#getkeyat) nebo [CRBTree::GetNext](#getnext) procházení stromu a načítat hodnoty.  
  
##  <a name="getkeyat"></a>  CRBTree::GetKeyAt  
 Volejte tuto metodu za účelem získání klíče z dané pozici ve stromu.  
  
```
const K& GetKeyAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 Hodnota pozice.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí klíč uložený na pozici *pos* ve stromové struktuře.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *pos* není platná pozice hodnotu, jsou výsledky nepředvídatelné. V sestavení pro ladění k selhání kontrolního výrazu dojde, pokud *pos* je rovna hodnotě NULL.  
  
##  <a name="getnext"></a>  CRBTree::GetNext  
 Volejte tuto metodu za účelem získání ukazatele na prvek uložený v `CRBTree` objektu a umístění, přejděte na další prvek.  
  
```
const CPair* GetNext(POSITION& pos) const throw();
CPair* GetNext(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 Čítač pozice vrácené předchozí volání metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na další [CPair](#cpair_class) hodnotu ve stromové struktuře.  
  
### <a name="remarks"></a>Poznámky  
 *Pos* pozice čítače je aktualizována po každém volání. Pokud je načtený element poslední ve stromové struktuře *pos* nastaven na hodnotu NULL.  
  
##  <a name="getnextassoc"></a>  CRBTree::GetNextAssoc  
 Volat tuto metodu za účelem získání klíč a hodnotu prvek uložený v objektu map a pozice, přejděte na další prvek.  
  
```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 Čítač pozice vrácené předchozí volání metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
 *Klíč*  
 Parametr šablony určující typ klíče stromové struktuře.  
  
 *value*  
 Parametr šablony určující typ hodnoty stromové struktuře.  
  
### <a name="remarks"></a>Poznámky  
 *Pos* pozice čítače je aktualizována po každém volání. Pokud je načtený element poslední ve stromové struktuře *pos* nastaven na hodnotu NULL.  
  
##  <a name="getnextkey"></a>  CRBTree::GetNextKey  
 Volejte tuto metodu za účelem získání klíče prvek uložený ve stromové struktuře a umístění, přejděte na další prvek.  
  
```
const K& GetNextKey(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 Čítač pozice vrácené předchozí volání metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na další klíče ve stromové struktuře.  
  
### <a name="remarks"></a>Poznámky  
 Aktualizuje aktuální pozice čítače, *pos*. Pokud nejsou žádné další položky ve stromové struktuře, čítač pozice je nastaven na hodnotu NULL.  
  
##  <a name="getnextvalue"></a>  CRBTree::GetNextValue  
 Volání této metody k získání hodnoty prvek uložený ve stromové struktuře a umístění, přejděte na další prvek.  
  
```
const V& GetNextValue(POSITION& pos) const throw();
V& GetNextValue(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 Čítač pozice vrácené předchozí volání metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na další hodnotu ve stromové struktuře.  
  
### <a name="remarks"></a>Poznámky  
 Aktualizuje aktuální pozice čítače, *pos*. Pokud nejsou žádné další položky ve stromové struktuře, čítač pozice je nastaven na hodnotu NULL.  
  
##  <a name="getprev"></a>  CRBTree::GetPrev  
 Volejte tuto metodu za účelem získání ukazatele na prvek uložený v `CRBTree` objektu a pak aktualizujte umístění na předchozí prvek.  
  
```
const CPair* GetPrev(POSITION& pos) const throw();
CPair* GetPrev(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 Čítač pozice vrácené předchozí volání metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrací ukazatel na předchozí [CPair](#cpair_class) hodnota uložená ve stromové struktuře.  
  
### <a name="remarks"></a>Poznámky  
 Aktualizuje aktuální pozice čítače, *pos*. Pokud nejsou žádné další položky ve stromové struktuře, čítač pozice je nastaven na hodnotu NULL.  
  
##  <a name="gettailposition"></a>  CRBTree::GetTailPosition  
 Volejte tuto metodu za účelem získání hodnoty pozice pro prvek na konec stromu.  
  
```
POSITION GetTailPosition() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu pozice pro prvek na konec stromu.  
  
### <a name="remarks"></a>Poznámky  
 Hodnota vrácená `GetTailPosition` lze použít s metodami, jako [CRBTree::GetKeyAt](#getkeyat) nebo [CRBTree::GetPrev](#getprev) procházení stromu a načítat hodnoty.  
  
##  <a name="getvalueat"></a>  CRBTree::GetValueAt  
 Volejte tuto metodu za účelem načtení hodnoty uložené na dané pozici v `CRBTree` objektu.  
  
```
const V& GetValueAt(POSITION pos) const throw();
V& GetValueAt(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 Čítač pozice vrácené předchozí volání metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na hodnotu uloženou v dané pozici v `CRBTree` objektu.  
  
##  <a name="isempty"></a>  CRBTree::IsEmpty  
 Volejte tuto metodu za účelem testování pro objekt prázdný strom.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud stromu je prázdné, hodnota FALSE v opačném případě.  
  
##  <a name="kinargtype"></a>  CRBTree::KINARGTYPE  
 Typ použitý klíč je předána jako vstupní argument.  
  
```
typedef KTraits::INARGTYPE KINARGTYPE;
```  
  
##  <a name="koutargtype"></a>  CRBTree::KOUTARGTYPE  
 Typ použitý při klíč se vrátí jako výstup argument.  
  
```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```  
  
##  <a name="removeall"></a>  CRBTree::RemoveAll  
 Voláním této metody lze odebrat všechny prvky z `CRBTree` objektu.  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vymaže navýšení kapacity `CRBTree` objektu, uvolňování paměti pro ukládání prvky.  
  
##  <a name="removeat"></a>  CRBTree::RemoveAt  
 Volejte tuto metodu za účelem odebrání elementu na dané pozici v `CRBTree` objektu.  
  
```
void RemoveAt(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 Čítač pozice vrácené předchozí volání metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
### <a name="remarks"></a>Poznámky  
 Odebere dvojice klíč/hodnota, které jsou uložené na zadané pozici. Je uvolněna paměť pro ukládání elementu. Odkazuje na POZICI *pos* stává neplatným a při pozice všech elementů ve stromové struktuře zůstává v platnosti, ne tedy nutně dělají zachovat stejné pořadí.  
  
##  <a name="setvalueat"></a>  CRBTree::SetValueAt  
 Voláním této metody lze změnit hodnotu uloženou v dané pozici v `CRBTree` objektu.  
  
```
void SetValueAt(POSITION pos, VINARGTYPE value);
```  
  
### <a name="parameters"></a>Parametry  
 *POS*  
 Čítač pozice vrácené předchozí volání metody, jako [CRBTree::GetHeadPosition](#getheadposition) nebo [CRBTree::FindFirstKeyAfter](#findfirstkeyafter).  
  
 *value*  
 Hodnota k přidání do `CRBTree` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Změní hodnotu prvek uložený na dané pozici v `CRBTree` objektu.  
  
##  <a name="vinargtype"></a>  CRBTree::VINARGTYPE  
 Typ použitý jako vstupní argument je předána hodnota.  
  
```
typedef VTraits::INARGTYPE VINARGTYPE;
```  
  
##  <a name="voutargtype"></a>  CRBTree::VOUTARGTYPE  
 Typ použitý při je hodnota předána jako argument výstup.  
  
```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```  
  
## <a name="see-also"></a>Viz také  
 [Přehled tříd](../../atl/atl-class-overview.md)
