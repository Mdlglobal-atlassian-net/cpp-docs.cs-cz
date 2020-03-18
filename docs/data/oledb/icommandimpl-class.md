---
title: ICommandImpl – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 6e095e01d3131f98b44935705b2564291fb13844
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447058"
---
# <a name="icommandimpl-class"></a>ICommandImpl – třída

Poskytuje implementaci pro rozhraní [ICommand](/previous-versions/windows/desktop/ms709737(v=vs.85)) .

## <a name="syntax"></a>Syntaxe

```cpp
template <class T, class CommandBase = ICommand>
class ATL_NO_VTABLE ICommandImpl : public CommandBase
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída odvozená od `ICommandImpl`.

*CommandBase*<br/>
Rozhraní příkazu. Výchozí formát je `ICommand`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Atldb. h

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Zrušení](#cancel)|Zruší aktuální spuštění příkazu.|
|[CancelExecution](#cancelexecution)|Zruší aktuální spuštění příkazu.|
|[CreateRowset](#createrowset)|Vytvoří objekt sady řádků.|
|[Execute](#execute)|Provede příkaz.|
|[GetDBSession](#getdbsession)|Vrátí ukazatel rozhraní na relaci, která vytvořila příkaz.|
|[ICommandImpl](#icommandimpl)|Konstruktor|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[m_bCancel](#bcancel)|Určuje, zda má být příkaz zrušen.|
|[m_bCancelWhenExecuting](#bcancelwhenexecuting)|Určuje, zda má být příkaz zrušen při spuštění.|
|[m_bIsExecuting](#bisexecuting)|Určuje, zda je příkaz aktuálně spuštěn.|

## <a name="remarks"></a>Poznámky

Povinné rozhraní objektu Command.

## <a name="cancel"></a>ICommandImpl:: Cancel

Zruší aktuální spuštění příkazu.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(Cancel)();
```

### <a name="remarks"></a>Poznámky

Viz [ICommand:: Cancel](/previous-versions/windows/desktop/ms714402(v=vs.85)) v *referenci programátora OLE DB*.

## <a name="cancelexecution"></a>ICommandImpl:: CancelExecution

Zruší aktuální spuštění příkazu.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT CancelExecution();
```

## <a name="createrowset"></a>ICommandImpl:: CreateRowset

Volá se [spuštěním, aby](../../data/oledb/icommandimpl-execute.md) se vytvořila jediná sada řádků.

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
Člen třídy šablony představující třídu sady řádků uživatele. Obvykle generuje průvodcem.

*pUnkOuter*<br/>
pro Ukazatel na řídicí `IUnknown` rozhraní, pokud se sada řádků vytváří jako součást agregace; v opačném případě má hodnotu null.

*riid*<br/>
pro Odpovídá *riid* v `ICommand::Execute`.

*pParams*<br/>
[in/out] Odpovídá *pParams* v `ICommand::Execute`.

*pcRowsAffected*<br/>
Odpovídá *pcRowsAffected* v `ICommand::Execute`.

*ppRowset*<br/>
[in/out] Odpovídá *ppRowset* v `ICommand::Execute`.

*pRowsetObj*<br/>
mimo Ukazatel na objekt sady řádků. Tento parametr se obvykle nepoužívá, ale je možné jej použít, je-li nutné provést více práce na sadě řádků předtím, než je předáte objektu COM. Životnost *pRowsetObj* je vázána *ppRowset*.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT. Seznam typických hodnot naleznete v tématu `ICommand::Execute`.

### <a name="remarks"></a>Poznámky

Chcete-li vytvořit více než jednu sadu řádků nebo zadat vlastní podmínky pro vytváření různých sad řádků, umístěte různá volání `CreateRowset` v rámci `Execute`.

Viz [ICommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) v *referenci programátora OLE DB.*

## <a name="execute"></a>ICommandImpl:: Execute

Provede příkaz.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT Execute(IUnknown* pUnkOuter,
   REFIID riid,
   DBPARAMS* pParams,
   DBROWCOUNT* pcRowsAffected,
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>Parametry

Viz [ICommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="remarks"></a>Poznámky

Požadované odchozí rozhraní bude rozhraní získaná z objektu sady řádků, který tato funkce vytvoří.

`Execute` volá [CreateRowset](../../data/oledb/icommandimpl-createrowset.md). Přepsat výchozí implementaci pro vytvoření více než jedné sady řádků nebo pro poskytnutí vlastních podmínek pro vytváření různých sad řádků.

## <a name="getdbsession"></a>ICommandImpl:: GetDBSession

Vrátí ukazatel rozhraní na relaci, která vytvořila příkaz.

### <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD (GetDBSession) (REFIID riid,
   IUnknown** ppSession);
```

#### <a name="parameters"></a>Parametry

Viz [ICommand:: GetDBSession](/previous-versions/windows/desktop/ms719622(v=vs.85)) v *referenci programátora OLE DB*.

### <a name="remarks"></a>Poznámky

Užitečné pro načítání vlastností z relace.

## <a name="icommandimpl"></a>ICommandImpl:: ICommandImpl

Konstruktor

### <a name="syntax"></a>Syntaxe

```cpp
ICommandImpl();
```

## <a name="bcancel"></a>ICommandImpl:: m_bCancel

Určuje, zda je příkaz zrušen.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned m_bCancel:1;
```

### <a name="remarks"></a>Poznámky

Tuto proměnnou můžete načíst v metodě `Execute` třídy Command a zrušit podle potřeby.

## <a name="bcancelwhenexecuting"></a>ICommandImpl:: m_bCancelWhenExecuting

Určuje, zda lze příkaz Zrušit při spuštění.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned m_bCancelWhenExecuting:1;
```

### <a name="remarks"></a>Poznámky

Výchozí **hodnota je true** (lze zrušit).

## <a name="bisexecuting"></a>ICommandImpl:: m_bIsExecuting

Určuje, zda je příkaz aktuálně spuštěn.

### <a name="syntax"></a>Syntaxe

```cpp
unsigned m_bIsExecuting:1;
```

### <a name="remarks"></a>Poznámky

Metoda `Execute` vaší třídy příkazu může tuto proměnnou nastavit na **hodnotu true**.

## <a name="see-also"></a>Viz také

[Šablony poskytovatele OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)