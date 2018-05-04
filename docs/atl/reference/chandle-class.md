---
title: Třída CHandle | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHandle
- ATLBASE/ATL::CHandle
- ATLBASE/ATL::CHandle::CHandle
- ATLBASE/ATL::CHandle::Attach
- ATLBASE/ATL::CHandle::Close
- ATLBASE/ATL::CHandle::Detach
- ATLBASE/ATL::CHandle::m_h
dev_langs:
- C++
helpviewer_keywords:
- CHandle class
ms.assetid: 883e9db5-40ec-4e29-9c74-4dd2ddd2e35d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b57aab927380f8801c3b9cab258a695c7d8a59d0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="chandle-class"></a>CHandle – třída
Tato třída poskytuje metody pro vytváření a používání objekt popisovače.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CHandle
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CHandle::CHandle](#chandle)|Konstruktor|  
|[CHandle:: ~ CHandle](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CHandle::Attach](#attach)|Volat tuto metodu za účelem připojení `CHandle` objekt, který má existující popisovač.|  
|[CHandle::Close](#close)|Voláním této metody lze zavřít `CHandle` objektu.|  
|[CHandle::Detach](#detach)|Volat tuto metodu za účelem odpojení popisovač z `CHandle` objektu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CHandle::operator POPISOVAČ](#operator_handle)|Vrací hodnotu uloženou popisovač.|  
|[CHandle::operator =](#operator_eq)|Operátor přiřazení.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CHandle::m_h](#m_h)|Členské proměnné, která uloží popisovač.|  
  
## <a name="remarks"></a>Poznámky  
 A `CHandle` objekt lze použít vždy, když je požadovaný popisovač: Hlavní rozdíl je, že `CHandle` objektu bude automaticky odstraněna.  
  
> [!NOTE]
>  Některé funkce rozhraní API použije hodnotu NULL jako prázdný nebo neplatný popisovač, jiné zase INVALID_HANDLE_VALUE. `CHandle` pouze používá hodnotu NULL a bude považovat INVALID_HANDLE_VALUE skutečné popisovač. Při volání rozhraní API, která lze vrátit INVALID_HANDLE_VALUE, byste měli zkontrolovat pro tuto hodnotu před voláním [CHandle::Attach](#attach) nebo předání do `CHandle` konstruktoru a místo toho předat hodnotu NULL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="attach"></a>  CHandle::Attach  
 Volat tuto metodu za účelem připojení `CHandle` objekt, který má existující popisovač.  
  
```
void Attach(HANDLE h) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `h`  
 `CHandle` bude převzít vlastnictví popisovač `h`.  
  
### <a name="remarks"></a>Poznámky  
 Přiřadí `CHandle` do objektu `h` zpracování. V sestavení ladí, bude-li vyvolána ATLASSERT `h` má hodnotu NULL. Není provedena žádná další kontrola o platnosti popisovač.  
  
##  <a name="chandle"></a>  CHandle::CHandle  
 Konstruktor  
  
```
CHandle() throw();
CHandle(CHandle& h) throw();
explicit CHandle(HANDLE h) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `h`  
 Popisovač existující nebo `CHandle`.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří novou `CHandle` objektu, volitelně pomocí existující popisovač nebo `CHandle` objektu.  
  
##  <a name="dtor"></a>  CHandle:: ~ CHandle  
 Destruktor.  
  
```
~CHandle() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Uvolní `CHandle` objekt voláním [CHandle::Close](#close).  
  
##  <a name="close"></a>  CHandle::Close  
 Voláním této metody lze zavřít `CHandle` objektu.  
  
```
void Close() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Zavře otevřený objekt popisovač. Pokud popisovač hodnotu NULL, což bude v případě **Zavřít** již byla volána, ATLASSERT, bude vyvolána v sestavení pro ladění.  
  
##  <a name="detach"></a>  CHandle::Detach  
 Volat tuto metodu za účelem odpojení popisovač z `CHandle` objektu.  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí popisovač odpojuje.  
  
### <a name="remarks"></a>Poznámky  
 Uvolní vlastnictví popisovač.  
  
##  <a name="m_h"></a>  CHandle::m_h  
 Členské proměnné, která uloží popisovač.  
  
```
HANDLE m_h;
```  
  
##  <a name="operator_eq"></a>  CHandle::operator =  
 Operátor přiřazení.  
  
```
CHandle& operator=(CHandle& h) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `h`  
 `CHandle` bude převzít vlastnictví popisovač `h`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí odkaz na nové `CHandle` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `CHandle` objekt aktuálně obsahuje popisovač, bude uzavřeno. `CHandle` Objekt, je předaná bude mít odkaz na jeho popisovač nastavena na hodnotu NULL. To zajistí, že dva `CHandle` objekty, nikdy neobsahuje stejné active popisovač.  
  
##  <a name="operator_handle"></a>  CHandle::operator POPISOVAČ  
 Vrací hodnotu uloženou popisovač.  
  
```  
operator HANDLE() const throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Vrací hodnotu uloženou v [CHandle::m_h](#m_h).  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
