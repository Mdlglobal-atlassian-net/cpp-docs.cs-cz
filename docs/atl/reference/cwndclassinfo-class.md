---
title: "Třída CWndClassInfo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWndClassInfo
- ATLWIN/ATL::CWndClassInfo
- ATLWIN/ATL::Register
- ATLWIN/ATL::m_atom
- ATLWIN/ATL::m_bSystemCursor
- ATLWIN/ATL::m_lpszCursorID
- ATLWIN/ATL::m_lpszOrigName
- ATLWIN/ATL::m_szAutoName
- ATLWIN/ATL::m_wc
- ATLWIN/ATL::pWndProc
dev_langs: C++
helpviewer_keywords: CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b07f6b12914e18f3f83abedf59742a8b7c7867b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cwndclassinfo-class"></a>CWndClassInfo – třída
Tato třída poskytuje metody pro registraci informace pro třídu okna.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CWndClassInfo
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|[Registrace](#register)|Zaregistruje třídu oken.|  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[m_atom](#m_atom)|Jednoznačně identifikuje třídu registrované oken.|  
|[m_bSystemCursor](#m_bsystemcursor)|Určuje, zda prostředek kurzoru odkazuje kurzoru systému nebo kurzoru obsažené v modulu prostředků.|  
|[m_lpszCursorID](#m_lpszcursorid)|Určuje název prostředku kurzoru.|  
|[m_lpszOrigName](#m_lpszorigname)|Obsahuje název existující třídy oken.|  
|[m_szAutoName](#m_szautoname)|Obsahuje název ATL generované třídy oken.|  
|[m_wc](#m_wc)|Uchovává informace o třídě okna v **WNDCLASSEX** struktura.|  
|[pWndProc](#pwndproc)|Body procedury okna existující třídy oken.|  
  
## <a name="remarks"></a>Poznámky  
 `CWndClassInfo`spravuje informace okno třídy. Obvykle použijete `CWndClassInfo` prostřednictvím jednoho z tři makra `DECLARE_WND_CLASS`, `DECLARE_WND_CLASS_EX`, nebo `DECLARE_WND_SUPERCLASS`, jak je popsáno v následující tabulce:  
  
|– Makro|Popis|  
|-----------|-----------------|  
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo`zaregistruje informace pro novou třídu okna.|  
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo`zaregistruje informace pro novou třídu okno, včetně parametrů třídy.|  
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo`zaregistruje informace pro okno třídu, která je založená na existující třídy, ale používá jiné časové období procedury. Tento postup se nazývá vytváření supertříd.|  
  
 Ve výchozím nastavení [CWindowImpl](../../atl/reference/cwindowimpl-class.md) zahrnuje `DECLARE_WND_CLASS` makro vytvořit okno založeno na třídě nové okno. DECLARE_WND_CLASS poskytuje výchozí styly a barvu pozadí ovládacího prvku. Pokud chcete určit styl a barva pozadí sami, odvozena třídě z `CWindowImpl` a zahrnout `DECLARE_WND_CLASS_EX` makra v definici vaší třídy.  
  
 Pokud chcete vytvořit okno podle existující třídy oken, odvozena třídě z `CWindowImpl` a zahrnout `DECLARE_WND_SUPERCLASS` makra v definici vaší třídy. Příklad:  
  
 [!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]  
  
 Další informace o třídách oken najdete v tématu [třídy oken](http://msdn.microsoft.com/library/windows/desktop/ms632596) ve Windows SDK.  
  
 Další informace o používání oken v ATL, najdete v článku [tříd oken ATL](../../atl/atl-window-classes.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
  
##  <a name="m_atom"></a>CWndClassInfo::m_atom  
 Obsahuje jedinečný identifikátor pro třídu registrované oken.  
  
```
ATOM m_atom;
```  
  
##  <a name="m_bsystemcursor"></a>CWndClassInfo::m_bSystemCursor  
 Pokud **TRUE**, systémový prostředek kurzoru budou načteny po registraci třídu oken.  
  
```
BOOL m_bSystemCursor;
```  
  
### <a name="remarks"></a>Poznámky  
 Prostředků kurzoru obsažené v modulu, jinak budou načteny.  
  
 `CWndClassInfo`používá `m_bSystemCursor` pouze tehdy, když [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (výchozí hodnota v [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) nebo [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) makro je zadán. V takovém případě `m_bSystemCursor` je inicializováno **TRUE**. Další informace najdete v tématu [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) Přehled.  
  
##  <a name="m_lpszcursorid"></a>CWndClassInfo::m_lpszCursorID  
 Určuje název prostředku kurzoru, nebo identifikátor prostředku v aplikaci word nejnižší a nula v aplikaci word vysokou pořadí.  
  
```
LPCTSTR m_lpszCursorID;
```  
  
### <a name="remarks"></a>Poznámky  
 Při registraci třídy oken, popisovač kurzor identifikovaný `m_lpszCursorID` je načíst a uložení [m_wc](#m_wc).  
  
 `CWndClassInfo`používá `m_lpszCursorID` pouze tehdy, když [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (výchozí hodnota v [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) nebo [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) makro je zadán. V takovém případě `m_lpszCursorID` je inicializováno **IDC_ARROW**. Další informace najdete v tématu [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) Přehled.  
  
##  <a name="m_lpszorigname"></a>CWndClassInfo::m_lpszOrigName  
 Obsahuje název existující třídy oken.  
  
```
LPCTSTR m_lpszOrigName;
```  
  
### <a name="remarks"></a>Poznámky  
 `CWndClassInfo`používá `m_lpszOrigName` pouze pokud zahrnete [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra v definici vaší třídy. V takovém případě `CWndClassInfo` zaregistruje třídu okna na základě třídy s názvem podle `m_lpszOrigName`. Další informace najdete v tématu [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) Přehled.  
  
##  <a name="m_szautoname"></a>CWndClassInfo::m_szAutoName  
 Obsahuje název třídy oken.  
  
```
TCHAR m_szAutoName[13];
```  
  
### <a name="remarks"></a>Poznámky  
 `CWndClassInfo`používá `m_szAutoName` pouze v případě **NULL** byla předána pro `WndClassName` parametru [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class), [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) nebo [ DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass). ATL se vytvořit název po registraci třídu oken.  
  
##  <a name="m_wc"></a>CWndClassInfo::m_wc  
 Uchovává informace o třídě okna v [WNDCLASSEX](http://msdn.microsoft.com/library/windows/desktop/ms633577) struktura.  
  
```
WNDCLASSEX m_wc;
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud jste zadali [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (výchozí hodnota v [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) nebo [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) makro, `m_wc` obsahuje informace o třídy oken s novou.  
  
 Pokud jste zadali [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makro, `m_wc` obsahuje informace o supertřídou – okno třídu, která je založená na existující třídy, ale používá jiné časové období procedury. [m_lpszOrigName](#m_lpszorigname) a [pWndProc](#pwndproc) uložit název existující třídy okno a postup okno, v uvedeném pořadí.  
  
##  <a name="pwndproc"></a>CWndClassInfo::pWndProc  
 Body procedury okna existující třídy oken.  
  
```
WNDPROC pWndProc;
```  
  
### <a name="remarks"></a>Poznámky  
 `CWndClassInfo`používá `pWndProc` pouze pokud zahrnete [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makra v definici vaší třídy. V takovém případě `CWndClassInfo` zaregistruje okno třídu, která je založená na existující třídy, ale používá jiné časové období procedury. Existující třída okna okno postup je uložen v `pWndProc`. Další informace najdete v tématu [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) Přehled.  
  
##  <a name="register"></a>CWndClassInfo::Register  
 Voláno rozhraním [CWindowImpl::Create](../../atl/reference/cwindowimpl-class.md#create) registrovat třídu okno, pokud ho ještě není zaregistrovaný.  
  
```
ATOM Register(WNDPROC* pProc);
```  
  
### <a name="parameters"></a>Parametry  
 `pProc`  
 [out] Určuje původní procedury okna existující třídy oken.  
  
### <a name="return-value"></a>Návratová hodnota  
 V případě úspěšného atom který jednoznačně identifikuje třídu oken registrována. Jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud jste zadali [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (výchozí hodnota v [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) nebo [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) makro, `Register` zaregistruje novou třídu okna. V takovém případě `pProc` parametr se nepoužívá.  
  
 Pokud jste zadali [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) makro, `Register` zaregistruje supertřídou – okno třídu, která je založená na existující třídy, ale používá jiné časové období procedury. Existující třída okna okno postup je vrácený v `pProc`.  
  
## <a name="see-also"></a>Viz také  
 [CComControl – třída](../../atl/reference/ccomcontrol-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)