---
title: Třída _U_STRINGorID | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
dev_langs:
- C++
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a601b1c64b28681c13a0b9e8f42156d8820cb4b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359659"
---
# <a name="ustringorid-class"></a>_U_STRINGorID – třída
Tato třída argument adaptér umožňuje buď názvy prostředků ( `LPCTSTR`s) nebo ID prostředku ( **Celé_číslo**s) mají být předány funkce bez nutnosti volající převést na řetězec pomocí ID **MAKEINTRESOURCE** makro.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class _U_STRINGorID
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[_U_STRINGorID::_U_STRINGorID](#_u_stringorid___u_stringorid)|Konstruktor|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|Identifikátor prostředku.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída slouží k implementaci obálky k rozhraní API správy prostředků Windows, jako [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042), [LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072), a [LoadMenu](http://msdn.microsoft.com/library/windows/desktop/ms647990) funkce, které přijímají `LPCTSTR` argument, který může být buď v názvu prostředku nebo jeho ID.  
  
 Třída definuje dvě přetížení konstruktor: jeden přijme `LPCTSTR` argument a dalších přijme **Celé_číslo** argument. **Celé_číslo** argument je převést na typ prostředku, který je kompatibilní s funkcí pro správu prostředků systému Windows pomocí **MAKEINTRESOURCE** makro a výsledek uložený v single – datový člen dané třídy, [m_lpstr](#_u_stringorid__m_lpstr). Argument `LPCTSTR` konstruktor ukládána přímo bez převodu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="_u_stringorid__m_lpstr"></a>  _U_STRINGorID::m_lpstr  
 Třída obsahuje hodnotu předanou buď jeho konstruktory jako veřejné `LPCTSTR` – datový člen.  
  
```
LPCTSTR m_lpstr;
```  
  
##  <a name="_u_stringorid___u_stringorid"></a>  _U_STRINGorID::_U_STRINGorID  
 **Celé_číslo** konstruktor převede její argument pro typ prostředku, který je kompatibilní s funkcí pro správu prostředků systému Windows pomocí **MAKEINTRESOURCE** makro a výsledek je uložen v jedné třídy – datový člen, [m_lpstr](#_u_stringorid__m_lpstr).  
  
```
_U_STRINGorID(UINT nID);  
_U_STRINGorID(LPCTSTR lpString);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 ID prostředku.  
  
 `lpString`  
 Název prostředku.  
  
### <a name="remarks"></a>Poznámky  
 Argument `LPCTSTR` konstruktor ukládána přímo bez převodu.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
