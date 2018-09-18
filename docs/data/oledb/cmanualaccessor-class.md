---
title: CManualAccessor – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- AddBindEntry
- CManualAccessor.AddBindEntry
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
- ATL::CManualAccessor::CreateAccessor
- CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
- ATL::CManualAccessor::CreateParameterAccessor
- ATL.CManualAccessor.CreateParameterAccessor
- CManualAccessor.CreateParameterAccessor
- CreateParameterAccessor
- CManualAccessor::CreateParameterAccessor
dev_langs:
- C++
helpviewer_keywords:
- CManualAccessor class
- AddBindEntry method
- AddParameterEntry method
- CreateAccessor method
- CreateParameterAccessor method
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 223b00f49a04cbc4305bdd14b26cd47bd8afb114
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104880"
---
# <a name="cmanualaccessor-class"></a>CManualAccessor – třída

Představuje typ přístupového objektu určený pro pokročilé uživatele.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CManualAccessor : public CAccessorBase  
```  

## <a name="requirements"></a>Požadavky  

**Záhlaví:** také atldbcli.h  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[AddBindEntry –](#addbindentry)|Přidá položku vazby výstupní sloupce.|  
|[AddParameterEntry](#addparameterentry)|Přidá položku parametru pro parametr přístupového objektu.|  
|[CreateAccessor –](#createaccessor)|Přiděluje paměť pro sloupec struktury vazby a inicializuje sloupec datové členy.|  
|[Createparameteraccessor –](#createparameteraccessor)|Přiděluje paměť pro parametr vazby struktury a inicializuje parametry datových členů.|  
  
## <a name="remarks"></a>Poznámky  

Pomocí `CManualAccessor`, můžete zadat parametr a výstupní vazba sloupce voláním funkce modulu runtime.  

## <a name="addbindentry"></a> CManualAccessor::AddBindEntry

Přidá položku vazby výstupní sloupce.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
void AddBindEntry(DBORDINAL nOrdinal,  
   DBTYPE wType,  DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [DBBINDING](/previous-versions/windows/desktop/ms716845\(v=vs.85\)) v *referenční informace pro OLE DB programátory*.  
  
*nOrdinal*<br/>
[in] Číslo sloupce.  
  
*wType*<br/>
[in] Datového typu.  
  
*nColumnSize*<br/>
[in] Sloupec velikost v bajtech.  
  
*pData*<br/>
[in] Ukazatel na sloupec data uložená ve vyrovnávací paměti.  
  
*pLength*<br/>
[in] Ukazatel na délku pole, podle potřeby.  
  
*pStatus*<br/>
[in] Ukazatel na proměnnou bylo vázané na sloupce stavu, v případě potřeby.  
  
### <a name="remarks"></a>Poznámky  

Pokud chcete používat tuto funkci, nejprve je třeba volat [CreateAccessor –](../../data/oledb/cmanualaccessor-createaccessor.md). Nelze přidat více položek než počet sloupců zadaný v `CreateAccessor`. 
  
## <a name="addparameterentry"></a> CManualAccessor::AddParameterEntry

Přidá položku parametr struktury vstupní parametr.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
void AddParameterEntry(DBORDINAL nOrdinal,  
   DBTYPE wType,  DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL,  
   DBPARAMIO eParamIO = DBPARAMIO_INPUT) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [DBBINDING](/previous-versions/windows/desktop/ms716845\(v=vs.85\)) v *referenční informace pro OLE DB programátory*.  
  
*nOrdinal*<br/>
[in] Počet parametrů.  
  
*wType*<br/>
[in] Datového typu.  
  
*nColumnSize*<br/>
[in] Sloupec velikost v bajtech.  
  
*pData*<br/>
[in] Ukazatel na sloupec data uložená ve vyrovnávací paměti.  
  
*pLength*<br/>
[in] Ukazatel na délku pole, podle potřeby.  
  
*pStatus*<br/>
[in] Ukazatel na proměnnou bylo vázané na sloupce stavu, v případě potřeby.  
  
*eParamIO*<br/>
[in] Určuje, zda je parametr, ke kterému je přidružené vazby vstupní, vstup/výstup nebo výstupní parametr.  
  
### <a name="remarks"></a>Poznámky  

Pokud chcete používat tuto funkci, nejprve je třeba volat [createparameteraccessor –](../../data/oledb/cmanualaccessor-createparameteraccessor.md). 

## <a name="createaccessor"></a> CManualAccessor::CreateAccessor

Přiděluje paměť pro sloupec struktury vazby a inicializuje sloupec datové členy.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateAccessor(int nBindEntries,   
  void* pBuffer,   
   DBLENGTH nBufferSize) throw();  
```  
  
#### <a name="parameters"></a>Parametry  

*nBindEntries*<br/>
[in] Počet sloupců. Tato hodnota by měla odpovídat počet volání [CManualAccessor::AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md) funkce.  
  
*pBuffer*<br/>
[in] Ukazatel do vyrovnávací paměti, kde se ukládají výstupní sloupce.  
  
*nBufferSize*<br/>
[in] Velikost vyrovnávací paměti v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  

Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  

Voláním této funkce před voláním `CManualAccessor::AddBindEntry` funkce.  

## <a name="createparameteraccessor"></a> CManualAccessor::CreateParameterAccessor

Přiděluje paměť pro parametr vazby struktury a inicializuje parametry datových členů.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CreateParameterAccessor(int nBindEntries,   
   void* pBuffer,   
   DBLENGTH nBufferSize) throw();  
```  
  
#### <a name="parameters"></a>Parametry  

*nBindEntries*<br/>
[in] Počet sloupců.  
  
*pBuffer*<br/>
[in] Ukazatel do vyrovnávací paměti, kde jsou uložené vstupní sloupce.  
  
*nBufferSize*<br/>
[in] Velikost vyrovnávací paměti v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  

Jeden standardní hodnoty HRESULT.  
  
### <a name="remarks"></a>Poznámky  

Před voláním této funkce musíte volat [AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md).

## <a name="see-also"></a>Viz také  

[DBViewer](../../visual-cpp-samples.md)<br/>
[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor – třída](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)