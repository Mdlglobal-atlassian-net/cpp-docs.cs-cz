---
title: CSession – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
- CSession.Abort
- CSession::Abort
- ATL.CSession.Abort
- ATL::CSession::Abort
- CSession::Close
- ATL.CSession.Close
- CSession.Close
- ATL::CSession::Close
- CSession.Commit
- ATL.CSession.Commit
- ATL::CSession::Commit
- CSession::Commit
- GetTransactionInfo
- CSession.GetTransactionInfo
- ATL.CSession.GetTransactionInfo
- CSession::GetTransactionInfo
- ATL::CSession::GetTransactionInfo
- ATL::CSession::Open
- CSession::Open
- CSession.Open
- ATL.CSession.Open
- CSession::StartTransaction
- StartTransaction
- ATL.CSession.StartTransaction
- CSession.StartTransaction
- ATL::CSession::StartTransaction
dev_langs:
- C++
helpviewer_keywords:
- CSession class
- Abort method
- Close method
- Commit method
- GetTransactionInfo method
- Open method
- StartTransaction method
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8cbfa7dc712755790b3a398db3377a8faccd4525
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49084019"
---
# <a name="csession-class"></a>CSession – třída

Představuje relaci izolovanou databázi přístup.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class CSession  
```  

## <a name="requirements"></a>Požadavky  

**Záhlaví:** také atldbcli.h  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Abort](#abort)|Zruší (končí) transakce.|  
|[Zavřít](#close)|Ukončení relace.|  
|[Potvrzení změn](#commit)|potvrzení transakce.|  
|[Gettransactioninfo –](#gettransactioninfo)|Vrátí informace o transakci.|  
|[Otevřít](#open)|Otevře se nová relace pro objekt zdroje dat.|  
|[StartTransaction –](#starttransaction)|Spustí novou transakci pro tuto relaci.|  
  
## <a name="remarks"></a>Poznámky  

Jeden nebo více relací může být přidružená k připojení každého poskytovatele (zdroj dat), která je reprezentována [CDataSource](../../data/oledb/cdatasource-class.md) objektu. Chcete-li vytvořit nový `CSession` pro `CDataSource`, volání [CSession::Open](../../data/oledb/csession-open.md). Začněte databázové transakce `CSession` poskytuje `StartTransaction` metody. Po zahájení transakce se mohou zavázat k jeho použití `Commit` metodu, nebo zrušit pomocí `Abort` metody.  
  
## <a name="abort"></a> CSession::Abort

Ukončí transakce.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Abort(BOID* pboidReason = NULL,   
   BOOL bRetaining = FALSE,   
   BOOL bAsync = FALSE) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [ITransaction::Abort](/previous-versions/windows/desktop/ms709833) v *referenční informace pro OLE DB programátory*.  
  
### <a name="return-value"></a>Návratová hodnota  

Standardní HRESULT. 

## <a name="close"></a> CSession::Close

Ukončí relaci, která byla otevírány [CSession::Open](../../data/oledb/csession-open.md).  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
void Close() throw();  
```  
  
### <a name="remarks"></a>Poznámky  

Verze `m_spOpenRowset` ukazatele.  

## <a name="commit"></a> CSession::Commit

potvrzení transakce.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Commit(BOOL bRetaining = FALSE,   
   DWORD grfTC = XACTTC_SYNC,   
   DWORD grfRM = 0) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [ITransaction::Commit](/previous-versions/windows/desktop/ms713008) v *referenční informace pro OLE DB programátory*.  
  
### <a name="return-value"></a>Návratová hodnota  

Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  

Další informace najdete v tématu [ITransaction::Commit](/previous-versions/windows/desktop/ms713008).  

## <a name="gettransactioninfo"></a> CSession::GetTransactionInfo

Vrátí informace o transakci.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetTransactionInfo(XACTTRANSINFO* pInfo) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [ITransaction::GetTransactionInfo](/previous-versions/windows/desktop/ms714975) v *referenční informace pro OLE DB programátory*.  
  
### <a name="return-value"></a>Návratová hodnota  

Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  

Další informace najdete v tématu [ITransaction::GetTransactionInfo](/previous-versions/windows/desktop/ms714975) v *OLE DB referenční informace pro programátory*. 

## <a name="open"></a> CSession::Open

Otevře se nová relace pro objekt zdroje dat.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Open(const CDataSource& ds,  
   DBPROPSET *pPropSet = NULL,  
   ULONG ulPropSets = 0) throw();  
```  
  
#### <a name="parameters"></a>Parametry  

*adresářové služby*<br/>
[in] Zdroj dat, pro který má být otevřeno relace.  
  
*pPropSet*<br/>
[in] Ukazatel na pole [DBPROPSET](/previous-versions/windows/desktop/ms714367) struktury obsahující vlastnosti a hodnoty, která se má nastavit. Zobrazit [sady vlastností a vlastností skupiny](/previous-versions/windows/desktop/ms713696) v *referenční informace pro OLE DB programátory* ve Windows SDK.  
  
*ulPropSets*<br/>
[in] Počet [DBPROPSET](/previous-versions/windows/desktop/ms714367) struktury předané *pPropSet* argument.  
  
### <a name="return-value"></a>Návratová hodnota  

Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  

Je nutné otevřít objekt zdroje dat pomocí [CDataSource::Open](../../data/oledb/cdatasource-open.md) před předáním do `CSession::Open`.  

## <a name="starttransaction"></a> CSession::StartTransaction

Spustí novou transakci pro tuto relaci.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT StartTransaction(ISOLEVEL isoLevel = ISOLATIONLEVEL_READCOMMITTED,  
   ULONG isoFlags = 0,  
   ITransactionOptions* pOtherOptions = NULL,  
   ULONG* pulTransactionLevel = NULL) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [ITransactionLocal::StartTransaction](/previous-versions/windows/desktop/ms709786) v *referenční informace pro OLE DB programátory*.  
  
### <a name="return-value"></a>Návratová hodnota  

Standardní HRESULT.  
  
### <a name="remarks"></a>Poznámky  

Další informace najdete v tématu [ITransactionLocal::StartTransaction](/previous-versions/windows/desktop/ms709786) v *OLE DB referenční informace pro programátory*. 
  
## <a name="see-also"></a>Viz také  

[CatDB](../../visual-cpp-samples.md)<br/>
[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)