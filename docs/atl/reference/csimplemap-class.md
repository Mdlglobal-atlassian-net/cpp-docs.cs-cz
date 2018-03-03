---
title: "Třída CSimpleMap | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayElementType
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayKeyType
- ATLSIMPCOLL/ATL::CSimpleMap::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::Add
- ATLSIMPCOLL/ATL::CSimpleMap::FindKey
- ATLSIMPCOLL/ATL::CSimpleMap::FindVal
- ATLSIMPCOLL/ATL::CSimpleMap::GetKeyAt
- ATLSIMPCOLL/ATL::CSimpleMap::GetSize
- ATLSIMPCOLL/ATL::CSimpleMap::GetValueAt
- ATLSIMPCOLL/ATL::CSimpleMap::Lookup
- ATLSIMPCOLL/ATL::CSimpleMap::Remove
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleMap::ReverseLookup
- ATLSIMPCOLL/ATL::CSimpleMap::SetAt
- ATLSIMPCOLL/ATL::CSimpleMap::SetAtIndex
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMap class
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 27e4fdad706ab9e586efe72663880646e6f50f11
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="csimplemap-class"></a>CSimpleMap – třída
Tato třída poskytuje podporu pro jednoduché mapování pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>  
class CSimpleMap
```  
  
#### <a name="parameters"></a>Parametry  
 `TKey`  
 Typ klíče elementu.  
  
 `TVal`  
 Typ elementu hodnotu.  
  
 `TEqual`  
 Objekt znak, který slouží k definování test rovnosti pro elementy typu `T`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleMap::_ArrayElementType](#_arrayelementtype)|TypeDef pro vybraný typ hodnoty.|  
|[CSimpleMap::_ArrayKeyType](#_arraykeytype)|TypeDef pro typ klíče.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleMap::CSimpleMap](#csimplemap)|Konstruktor|  
|[CSimpleMap:: ~ CSimpleMap](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSimpleMap::Add](#add)|Přidá klíč a přidružené hodnoty pole mapování.|  
|[CSimpleMap::FindKey](#findkey)|Vyhledá konkrétního klíče.|  
|[CSimpleMap::FindVal](#findval)|Vyhledá určitou hodnotu.|  
|[CSimpleMap::GetKeyAt](#getkeyat)|Načte zadaný klíč.|  
|[CSimpleMap::GetSize](#getsize)|Vrátí počet položek v poli mapování.|  
|[CSimpleMap::GetValueAt](#getvalueat)|Načte zadanou hodnotu.|  
|[CSimpleMap::Lookup](#lookup)|Vrátí hodnotu spojené s daným klíčem.|  
|[CSimpleMap::Remove](#remove)|Odebere klíč a odpovídající hodnotu.|  
|[CSimpleMap::RemoveAll](#removeall)|Odebere všechny klíče a hodnoty.|  
|[CSimpleMap::RemoveAt](#removeat)|Odebere konkrétního klíče a odpovídající hodnotu.|  
|[CSimpleMap::ReverseLookup](#reverselookup)|Vrátí klíč přidružený k dané hodnotě.|  
|[CSimpleMap::SetAt](#setat)|Nastaví hodnotu spojené s daným klíčem.|  
|[CSimpleMap::SetAtIndex](#setatindex)|Nastaví konkrétní klíč a hodnotu.|  
  
## <a name="remarks"></a>Poznámky  
 `CSimpleMap`poskytuje podporu pro jednoduché mapování pole daného typu `T`, Správa neuspořádaný pole klíčové prvky a jejich přidružené hodnoty.  
  
 Parametr `TEqual` poskytuje způsob definování rovnosti funkce pro dva elementy typu `T`. Vytvořením třídy podobné [CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md), je možné změnit chování test rovnosti pro jakékoli dané pole. Například při plánování práce s pole ukazatele, může být užitečné k definování rovnosti jako v závislosti na hodnoty, které odkazují ukazatele. Výchozí implementace využívá **operator==()**.  
  
 Obě `CSimpleMap` a [CSimpleArray](../../atl/reference/csimplearray-class.md) jsou zadaná pro kompatibilitu s předchozí ATL uvolní a dokončení a efektivní implementace kolekce jsou poskytovány [CAtlArray](../../atl/reference/catlarray-class.md) a [ CAtlMap](../../atl/reference/catlmap-class.md).  
  
 Na rozdíl od jiných mapy kolekcí v ATL a MFC Tato třída implementuje pomocí jednoduchých polí a hledání vyhledávání vyžadovat lineárního hledání. `CAtlMap`by měl být použit při pole obsahuje velký počet elementů.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsimpcoll.h  
  
## <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]  
  
##  <a name="add"></a>CSimpleMap::Add  
 Přidá klíč a přidružené hodnoty pole mapování.  
  
```
BOOL Add(const TKey& key, const TVal& val);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klíč  
  
 *Val*  
 Přidružené hodnoty.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud klíč a hodnotu byly úspěšně přidal, FALSE, jinak hodnota.  
  
### <a name="remarks"></a>Poznámky  
 Každý pár klíč a hodnotu přidat mapování pole paměti uvolněno a znovu přidělit, aby se zajistilo, že jsou data pro každou vždycky uložena souvisle příčiny. To znamená druhý klíčovým prvkem vždy přímo odpovídá první prvek klíče v paměti a tak dále.  
  
##  <a name="_arrayelementtype"></a>CSimpleMap::_ArrayElementType  
 Definice typu pro typ klíče.  
  
```
typedef TVal _ArrayElementType;
```  
  
##  <a name="_arraykeytype"></a>CSimpleMap::_ArrayKeyType  
 Definice typu pro typ hodnoty.  
  
```
typedef TKey _ArrayKeyType;
```  
  
##  <a name="csimplemap"></a>CSimpleMap::CSimpleMap  
 Konstruktor  
  
```
CSimpleMap();
```  
  
### <a name="remarks"></a>Poznámky  
 Inicializuje datových členů.  
  
##  <a name="dtor"></a>CSimpleMap:: ~ CSimpleMap  
 Destruktor.  
  
```
~CSimpleMap();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní všechny přidělené prostředky.  
  
##  <a name="findkey"></a>CSimpleMap::FindKey  
 Vyhledá konkrétního klíče.  
  
```
int FindKey(const TKey& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klíč k vyhledání.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí index klíče Pokud najde, v opačném případě vrátí hodnotu -1.  
  
##  <a name="findval"></a>CSimpleMap::FindVal  
 Vyhledá určitou hodnotu.  
  
```
int FindVal(const TVal& val) const;
```  
  
### <a name="parameters"></a>Parametry  
 *Val*  
 Hodnota, pro které chcete vyhledat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí že index hodnoty pokud zjistí, v opačném případě vrátí hodnotu -1.  
  
##  <a name="getkeyat"></a>CSimpleMap::GetKeyAt  
 Načte klíče v zadaném indexu.  
  
```
TKey& GetKeyAt(int nIndex) const;
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index klíče, který se vrátí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí klíč odkazuje `nIndex`.  
  
### <a name="remarks"></a>Poznámky  
 Index předaná `nIndex` musí být platná pro návratovou hodnotu smysluplné.  
  
##  <a name="getsize"></a>CSimpleMap::GetSize  
 Vrátí počet položek v poli mapování.  
  
```
int GetSize() const;
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí počet položek (klíče a hodnoty je jedna položka) v poli mapování.  
  
##  <a name="getvalueat"></a>CSimpleMap::GetValueAt  
 Načte hodnotu konkrétní indexem.  
  
```
TVal& GetValueAt(int nIndex) const;
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index hodnota, která má vrátit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu odkazuje `nIndex`.  
  
### <a name="remarks"></a>Poznámky  
 Index předaná `nIndex` musí být platná pro návratovou hodnotu smysluplné.  
  
##  <a name="lookup"></a>CSimpleMap::Lookup  
 Vrátí hodnotu spojené s daným klíčem.  
  
```
TVal Lookup(const TKey& key) const;
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klíč  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí související hodnotu. Pokud není žádný odpovídající klíč nalezen, NULL, je vrácena.  
  
##  <a name="remove"></a>CSimpleMap::Remove  
 Odebere klíč a odpovídající hodnotu.  
  
```
BOOL Remove(const TKey& key);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klíč  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud klíč a odpovídající hodnotu, byly úspěšně odebrána, FALSE, jinak hodnota.  
  
##  <a name="removeall"></a>CSimpleMap::RemoveAll  
 Odebere všechny klíče a hodnoty.  
  
```
void RemoveAll();
```  
  
### <a name="remarks"></a>Poznámky  
 Odebere všechny klíče a hodnoty z objektu mapování pole.  
  
##  <a name="removeat"></a>CSimpleMap::RemoveAt  
 Odebere klíč a přidružené hodnoty v zadaném indexu.  
  
```
BOOL RemoveAt(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index klíče a přidružené hodnoty. Chcete-li odebrat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu, FALSE, pokud zadaný index je neplatný index.  
  
##  <a name="reverselookup"></a>CSimpleMap::ReverseLookup  
 Vrátí klíč přidružený k dané hodnotě.  
  
```
TKey ReverseLookup(const TVal& val) const;
```  
  
### <a name="parameters"></a>Parametry  
 *Val*  
 Hodnota  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí přidružený klíč. Pokud není žádný odpovídající klíč nalezen, NULL, je vrácena.  
  
##  <a name="setat"></a>CSimpleMap::SetAt  
 Nastaví hodnotu spojené s daným klíčem.  
  
```
BOOL SetAt(const TKey& key, const TVal& val);
```  
  
### <a name="parameters"></a>Parametry  
 `key`  
 Klíč  
  
 *Val*  
 Nová hodnota přiřadit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud byl nalezen klíč, a hodnota byla úspěšně změnil, FALSE, jinak hodnota.  
  
##  <a name="setatindex"></a>CSimpleMap::SetAtIndex  
 Nastaví klíč a hodnotu na zadaný index.  
  
```
BOOL SetAtIndex(  
    int nIndex,
    const TKey& key,
    const TVal& val);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index, odkazy na klíč a hodnotu párování změnit.  
  
 `key`  
 Nový klíč.  
  
 *Val*  
 Nová hodnota.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE Pokud úspěšné, FALSE, pokud nebyla platná index.  
  
### <a name="remarks"></a>Poznámky  
 Aktualizuje klíč a hodnotu, na kterou odkazuje `nIndex`.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
