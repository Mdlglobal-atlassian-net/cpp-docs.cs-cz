---
title: IRowsetNotifyImpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetNotifyImpl
- ATL::IRowsetNotifyImpl
- IRowsetNotifyImpl
- IRowsetNotifyImpl.OnFieldChange
- IRowsetNotifyImpl::OnFieldChange
- OnFieldChange
- IRowsetNotifyImpl::OnRowChange
- IRowsetNotifyImpl.OnRowChange
- OnRowChange
- OnRowsetChange
- IRowsetNotifyImpl::OnRowsetChange
- IRowsetNotifyImpl.OnRowsetChange
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyImpl class
- OnFieldChange method
- OnRowChange method
- OnRowsetChange method
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 771e35fecdf477aaaacb92c1ae34ba79e9aa2354
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42466407"
---
# <a name="irowsetnotifyimpl-class"></a>IRowsetNotifyImpl – třída
Implementuje a zaregistruje [IRowsetNotify](/previous-versions/windows/desktop/ms712959\(v=vs.85\)) na spotřebitele (označované také jako "jímka") tak, aby se zpracování oznámení.  
  
## <a name="syntax"></a>Syntaxe

```cpp
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify  
```  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[Onfieldchange –](#onfieldchange)|Upozorní příjemce všechny změny hodnoty sloupce.|  
|[OnRowChange](#onrowchange)|Upozorní příjemce změny první řádek nebo sady změn, které má vliv na celý řádek.|  
|[OnRowsetChange](#onrowsetchange)|Oznámí uživateli všechny změny, které mají vliv celá sada řádků.|  
  
## <a name="remarks"></a>Poznámky  
 Zobrazit [příjem oznámení](../../data/oledb/receiving-notifications.md) o implementaci rozhraní bod připojení pro příjemce.  
  
 `IRowsetNotifyImpl` poskytuje implementaci pro fiktivní `IRowsetNotify`, s prázdné funkce pro `IRowsetNotify` metody [onfieldchange –](/previous-versions/windows/desktop/ms715961\(v=vs.85\)), [onrowchange –](/previous-versions/windows/desktop/ms722694\(v=vs.85\)), a [onrowsetchange –](/previous-versions/windows/desktop/ms722669\(v=vs.85\)). Pokud je zděděn z této třídy při implementaci `IRowsetNotify` rozhraní, můžete implementovat pouze metody, které potřebujete. Také budete muset poskytnout prázdná implementace pro jiné metody sami.  

## <a name="onfieldchange"></a> IRowsetNotifyImpl::OnFieldChange
Upozorní příjemce všechny změny hodnoty sloupce.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(OnFieldChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ HROW /* hRow */,  
/* [in] */ DBORDINAL /* cColumns */,  
/* [size_is][in] */ DBORDINAL /* rgColumns */ [] ,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961\(v=vs.85\)) pro popisy parametrů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Zobrazit [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961\(v=vs.85\)) pro vrácení hodnoty popisy.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda zabalí [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961\(v=vs.85\)) metody. Viz popis v této metodě v OLE DB programátora odkaz podrobnosti.  

## <a name="onrowchange"></a> IRowsetNotifyImpl::OnRowChange
Upozorní příjemce změny první řádek nebo sady změn, které má vliv na celý řádek.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(OnRowChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBCOUNTITEM /* cRows */,  
/* [size_is][in] */ const HROW /* rghRows*/ [] ,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694\(v=vs.85\)) pro popisy parametrů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Zobrazit [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694\(v=vs.85\)) pro vrácení hodnoty popisy.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda zabalí [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694\(v=vs.85\)) metody. Viz popis v této metodě v OLE DB programátora odkaz podrobnosti. 

## <a name="onrowsetchange"></a> IRowsetNotifyImpl::OnRowsetChange
Oznámí uživateli všechny změny, které mají vliv celá sada řádků.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
STDMETHOD(OnRowsetChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>Parametry  
 Zobrazit [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669\(v=vs.85\)) pro popisy parametrů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Zobrazit [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669\(v=vs.85\)) pro vrácení hodnoty popisy.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda zabalí [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669\(v=vs.85\)) metody. Viz popis v této metodě v OLE DB programátora odkaz podrobnosti.
  
## <a name="see-also"></a>Viz také  
 [OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [IRowsetNotify](/previous-versions/windows/desktop/ms712959\(v=vs.85\))   
 [IRowsetNotifyCP – třída](../../data/oledb/irowsetnotifycp-class.md)