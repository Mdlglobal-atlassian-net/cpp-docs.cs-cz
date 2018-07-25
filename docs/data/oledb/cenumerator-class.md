---
title: CEnumerator – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CEnumerator
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
dev_langs:
- C++
helpviewer_keywords:
- CEnumerator class
- Find method
- GetMoniker method
- Open method
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9f8af45082f8b861b177c4e214a69e9b15799dd7
ms.sourcegitcommit: b217daee32d3413cf33753d9b4dc35a0022b1bfa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233370"
---
# <a name="cenumerator-class"></a>CEnumerator – třída
Používá objekt enumerátoru OLE DB, která zveřejní [ISourcesRowset](https://msdn.microsoft.com/library/ms715969.aspx) rozhraní vrátit sadu řádků s popisem všechny zdroje dat a enumerátory.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CEnumerator :   
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>  
```  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Najít](#find)|Hledá v rámci (zdroje dat) dostupných poskytovatelů vyhledávání pro jeden se zadaným názvem.|  
|[GetMoniker](#getmoniker)|Načte `IMoniker` rozhraní pro požadovaný aktuální záznam.|  
|[Otevřít](#open)|Otevře se enumerátor.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete načíst `ISourcesRowset` data nepřímo z této třídy.  

## <a name="find"></a> CEnumerator::Find
Vyhledá zadaný název mezi dostupných zprostředkovatelů.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
      bool Find(TCHAR* szSearchName) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *szSearchName*  
 [in] Název, který se má hledat.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE** Pokud název nebyl nalezen. V opačném případě **false**.  
  
### <a name="remarks"></a>Poznámky  
 Tento název se mapuje `SOURCES_NAME` člena [ISourcesRowset](https://msdn.microsoft.com/library/ms715969.aspx) rozhraní.  
  
## <a name="getmoniker"></a> CEnumerator::GetMoniker
Analyzuje zobrazovaný název na extrahuje komponentu řetězec, který lze převést na moniker.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();  


HRESULT GetMoniker(LPMONIKER* ppMoniker,   
   LPCTSTR lpszDisplayName) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *ppMoniker*  
 [out] Moniker služby byl analyzován ze zobrazovaného jména ([CEnumeratorAccessor::m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)) aktuálního řádku.  
  
 *lpszDisplayName*  
 [in] Zobrazovaný název analyzovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  

## <a name="open"></a> CEnumerator::Open
Vazeb zástupný název čítače, pokud jeden je zadán, pak načte sada řádků pro enumerátor voláním [ISourcesRowset::GetSourcesRowset](https://msdn.microsoft.com/library/ms711200.aspx).  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Open(LPMONIKER pMoniker) throw();  


HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();  


HRESULT Open(const CEnumerator& enumerator) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *pMoniker*  
 [in] Ukazatel na moniker enumerátor.  
  
 *pClsid*  
 [in] Ukazatel `CLSID` čítače.  
  
 *Enumerátor*  
 [in] Odkaz na enumerátor.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní HRESULT.  
  
## <a name="see-also"></a>Viz také  
 [DBViewer](../../visual-cpp-samples.md)   
 [OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)