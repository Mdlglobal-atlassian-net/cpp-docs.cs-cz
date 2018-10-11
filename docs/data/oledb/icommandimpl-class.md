---
title: Icommandimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandImpl
- ICommandImpl::Cancel
- Cancel
- ICommandImpl.Cancel
- ICommandImpl::CancelExecution
- ATL::ICommandImpl::CancelExecution
- ATL.ICommandImpl.CancelExecution
- CancelExecution
- ICommandImpl.CancelExecution
- ICommandImpl::CreateRowset
- ICommandImpl.CreateRowset
- CreateRowset
- ICommandImpl::Execute
- ICommandImpl.Execute
- ICommandImpl::GetDBSession
- GetDBSession
- ICommandImpl.GetDBSession
- ATL.ICommandImpl.ICommandImpl
- ATL::ICommandImpl::ICommandImpl
- ICommandImpl
- ICommandImpl::ICommandImpl
- ICommandImpl.ICommandImpl
- ICommandImpl::m_bCancel
- ICommandImpl.m_bCancel
- m_bCancel
- ATL::ICommandImpl::m_bCancel
- ATL.ICommandImpl.m_bCancel
- ICommandImpl::m_bCancelWhenExecuting
- ICommandImpl.m_bCancelWhenExecuting
- ATL::ICommandImpl::m_bCancelWhenExecuting
- m_bCancelWhenExecuting
- ATL.ICommandImpl.m_bCancelWhenExecuting
- ICommandImpl.m_bIsExecuting
- ATL::ICommandImpl::m_bIsExecuting
- m_bIsExecuting
- ATL.ICommandImpl.m_bIsExecuting
- ICommandImpl::m_bIsExecuting
dev_langs:
- C++
helpviewer_keywords:
- ICommandImpl class
- Cancel method
- CancelExecution method
- CreateRowset method
- Execute method
- GetDBSession method
- ICommandImpl constructor
- ICommandImpl class, constructor
- m_bCancel
- m_bCancelWhenExecuting
- m_bIsExecuting
ms.assetid: ef285fef-0d66-45e6-a762-b03357098e3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5f04104aadc2897118a402a06d93db27a5a16079
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082810"
---
# <a name="icommandimpl-class"></a>ICommandImpl – třída

Poskytuje implementaci pro [rozhraní ICommand](/previous-versions/windows/desktop/ms709737) rozhraní.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class CommandBase = ICommand>   
class ATL_NO_VTABLE ICommandImpl : public CommandBase  
```  
  
### <a name="parameters"></a>Parametry  

*T*<br/>
Vaše třída odvozena od `ICommandImpl`.  
  
*CommandBase*<br/>
Příkaz rozhraní. Výchozí hodnota je `ICommand`.  

## <a name="requirements"></a>Požadavky  

**Záhlaví:** atldb.h  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Zrušení](#cancel)|Zruší aktuální provedení příkazu.|  
|[Cancelexecution –](#cancelexecution)|Zruší aktuální provedení příkazu.|  
|[Createrowset –](#createrowset)|Vytvoří objekt sady řádků.|  
|[Execute](#execute)|Vykoná příkaz.|  
|[Getdbsession –](#getdbsession)|Vrátí ukazatel rozhraní na relaci, která vytvoří příkaz.|  
|[Icommandimpl –](#icommandimpl)|Konstruktor|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_bCancel](#bcancel)|Označuje, zda je příkazu budou zrušeny.|  
|[m_bCancelWhenExecuting](#bcancelwhenexecuting)|Označuje, zda je příkazu budou zrušeny při provádění.|  
|[m_bIsExecuting](#bisexecuting)|Určuje, zda příkaz právě probíhá.|  
  
## <a name="remarks"></a>Poznámky  

Povinné rozhraní pro objekt příkazu.  
  
## <a name="cancel"></a> ICommandImpl::Cancel

Zruší aktuální provedení příkazu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(Cancel)();  
```  
  
### <a name="remarks"></a>Poznámky  

Zobrazit [ICommand::Cancel](/previous-versions/windows/desktop/ms714402) v *referenční informace pro OLE DB programátory*.  

## <a name="cancelexecution"></a> ICommandImpl::CancelExecution

Zruší aktuální provedení příkazu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT CancelExecution();  
```  

## <a name="createrowset"></a> ICommandImpl::CreateRowset

Volané [Execute](../../data/oledb/icommandimpl-execute.md) k vytvoření jedné sady řádků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
template template <class RowsetClass>  
HRESULT CreateRowset(IUnknown* pUnkOuter,  
   REFIID riid,  
   DBPARAMS* pParams,  
   DBROWCOUNT* pcRowsAffected,  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj);  
```  
  
#### <a name="parameters"></a>Parametry  

*RowsetClass*<br/>
Šablona člena třídy představující třídu sady řádků uživatele. Obvykle generované průvodcem knihovnou.  
  
*pUnkOuter*<br/>
[in] Ukazatel řízení `IUnknown` rozhraní, pokud v sadě řádků se vytváří jako součást agregace; jinak má hodnotu null.  
  
*riid*<br/>
[in] Odpovídá *riid* v `ICommand::Execute`.  
  
*pParams*<br/>
[/ out] Odpovídá *pParams* v `ICommand::Execute`.  
  
*pcRowsAffected*<br/>
Odpovídá *pcRowsAffected* v `ICommand::Execute`.  
  
*ppRowset*<br/>
[/ out] Odpovídá *ppRowset* v `ICommand::Execute`.  
  
*pRowsetObj*<br/>
[out] Ukazatel na objektu sady řádků. Tento parametr se obvykle nepoužívá, ale lze použít, pokud před předáním objektu COM je nutné provést další práce na dané sadě řádků. Životnost *pRowsetObj* je svázaná s *ppRowset*.  
  
### <a name="return-value"></a>Návratová hodnota  

Standardní hodnoty HRESULT. Zobrazit `ICommand::Execute` seznam typické hodnoty.  
  
### <a name="remarks"></a>Poznámky  

Chcete-li vytvořit více než jedné sady řádků nebo poskytnout vlastní podmínky pro vytváření různých sad řádků, umístěte volání různých `CreateRowset` zevnitř `Execute`.  
  
Zobrazit [ICommand::Execute](/previous-versions/windows/desktop/ms718095) v *referenční informace pro OLE DB programátory.*  

## <a name="execute"></a> ICommandImpl::Execute

Vykoná příkaz.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT Execute(IUnknown* pUnkOuter,  
   REFIID riid,  
   DBPARAMS* pParams,  
   DBROWCOUNT* pcRowsAffected,  
   IUnknown** ppRowset);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [ICommand::Execute](/previous-versions/windows/desktop/ms718095) v *referenční informace pro OLE DB programátory*.  
  
### <a name="remarks"></a>Poznámky  

Odchozí požadované rozhraní bude rozhraní získaných z objektu sady řádků, které tato funkce vytvoří.  
  
`Execute` volání [createrowset –](../../data/oledb/icommandimpl-createrowset.md). Přepište výchozí implementace vytvořit více než jedné sady řádků nebo poskytnout vlastní podmínky pro vytváření různé sady řádků.  

## <a name="getdbsession"></a> ICommandImpl::GetDBSession

Vrátí ukazatel rozhraní na relaci, která vytvoří příkaz.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD (GetDBSession) (REFIID riid,  
   IUnknown** ppSession);  
```  
  
#### <a name="parameters"></a>Parametry  

Zobrazit [ICommand::GetDBSession](/previous-versions/windows/desktop/ms719622) v *referenční informace pro OLE DB programátory*.  
  
### <a name="remarks"></a>Poznámky  

Užitečné při načítání vlastností z relace.  

## <a name="icommandimpl"></a> ICommandImpl::ICommandImpl

Konstruktor  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
ICommandImpl();  
```  

## <a name="bcancel"></a> ICommandImpl::m_bCancel

Určuje, zda je příkaz zrušen.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
unsigned m_bCancel:1;  
```  
  
### <a name="remarks"></a>Poznámky  

V této proměnné můžete načíst `Execute` metody třídy příkazu a zrušit podle potřeby. 

## <a name="bcancelwhenexecuting"></a> ICommandImpl::m_bCancelWhenExecuting

Určuje, zda příkaz se může týkat při provádění.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
unsigned m_bCancelWhenExecuting:1;  
```  
  
### <a name="remarks"></a>Poznámky  

Výchozí hodnota je **true** (může být zrušen).  

## <a name="bisexecuting"></a> ICommandImpl::m_bIsExecuting

Určuje, zda příkaz právě probíhá.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
unsigned m_bIsExecuting:1;  
```  
  
### <a name="remarks"></a>Poznámky  

`Execute` Metoda třídy příkazu můžete tuto proměnnou nastavit na **true**. 
  
## <a name="see-also"></a>Viz také  

[Šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)