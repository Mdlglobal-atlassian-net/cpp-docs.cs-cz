---
title: "Okno třída makra | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
dev_langs: C++
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bba4b6743477ae3c3d345a20f1c2e672e73261e2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="window-class-macros"></a>Okno makra – třída
Tyto makra definovat okno třída nástrojů.  
  
|||  
|-|-|  
|[DECLARE_WND_CLASS](#declare_wnd_class)|Umožňuje zadat název třídy nové okno.| 
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017) Umožňuje zadat název nové třídy okno a nadřazených třídu, jejíž procedury okna budou používat novou třídu.| 
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|Umožňuje zadat název existující třídy okno na kterém bude na základě novou třídu okna.|  
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|Umožňuje zadat parametry třídy.|  

## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlwin.h  
   
##  <a name="declare_wnd_class"></a>DECLARE_WND_CLASS  
 Umožňuje zadat název třídy nové okno. Třída ovládacích prvků ovládacího prvku ActiveX knihovny ATL umístíte tento makro.  
  
```
DECLARE_WND_CLASS( WndClassName )
```  
  
### <a name="parameters"></a>Parametry  
 `WndClassName`  
 [v] Název třídy pro nové okno. Pokud **NULL**, ATL vygeneruje název třídy oken.  
  
### <a name="remarks"></a>Poznámky  
 Pokud používáte /permissive-compiler možnost, pak DECLARE_WND_CLASS způsobí chybu kompilátoru; Místo toho použijte DECLARE_WND_CLASS2.
 
 DECLARE_WND_CLASS umožňuje zadat název nové třídy okno, jejichž informace bude spravovat [CWndClassInfo](cwndclassinfo-class.md). `DECLARE_WND_CLASS`Definuje novou třídu okno implementací statické následující funkce:  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 `DECLARE_WND_CLASS`Určuje následující styly pro nové okno:  
  
-   CS_HREDRAW  
  
-   CS_VREDRAW  
  
-   CS_DBLCLKS  
  
 `DECLARE_WND_CLASS`také určuje barvu pozadí výchozím okně. Použití [DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) makro a poskytnout vám ve vlastních stylech barva pozadí.  
  
 [CWindowImpl](cwindowimpl-class.md) používá `DECLARE_WND_CLASS` makro vytvořit okno založeno na třídě nové okno. Chcete-li toto chování potlačit, použijte [DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) makro, nebo zadejte vlastní implementaci [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) funkce.  

  
 Další informace o používání oken v ATL, najdete v článku [tříd oken ATL](../../atl/atl-window-classes.md).  

##  <a name="declare_wnd_class2"></a>DECLARE_WND_CLASS2  
 (Visual Studio 2017) Podobá DECLARE_WND_CLASS, ale se speciálním parametrem, který zabraňuje závislé název chyby při kompilaci s /permissive-option.
  
```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```  
  
### <a name="parameters"></a>Parametry  
 `WndClassName`  
 [v] Název třídy pro nové okno. Pokud **NULL**, ATL vygeneruje název třídy oken. 

 `EnclosingClass`  
 [v] Název třídy oken, která obklopuje novou třídu okna. Nemůže být **NULL**.  
  
### <a name="remarks"></a>Poznámky 
Pokud používáte /permissive-option, pak DECLARE_WND_CLASS způsobí chybu kompilace protože obsahuje název závislé. DECLARE_WND_CLASS2 vyžaduje, abyste výslovně název třídy, že tento makro se používá v a nedojde k chybě v části /permissive-flag.
V opačném případě je stejný jako tento makro [DECLARE_WND_CLASS](#declare_wnd_class).
   
##  <a name="declare_wnd_superclass"></a>DECLARE_WND_SUPERCLASS  
 Umožňuje zadat parametry třídy. Třída ovládacích prvků ovládacího prvku ActiveX knihovny ATL umístíte tento makro.  
  
```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```  
  
### <a name="parameters"></a>Parametry  
 `WndClassName`  
 [v] Název okna třídy, že bude supertřídě `OrigWndClassName`. Pokud **NULL**, ATL vygeneruje název třídy oken.  
  
 `OrigWndClassName`  
 [v] Název existující třídy oken.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro umožňuje zadat název třídy oken, která bude supertřídě existující třídy oken. [CWndClassInfo](cwndclassinfo-class.md) spravuje informace nadřazené třídy.  
  
 `DECLARE_WND_SUPERCLASS`implementuje statické následující funkce:  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 Ve výchozím nastavení [CWindowImpl](cwindowimpl-class.md) používá [DECLARE_WND_CLASS](#declare_wnd_class) makro vytvořit okno založeno na třídě nové okno. Zadáním `DECLARE_WND_SUPERCLASS` makro v `CWindowImpl`-odvozené třídy, třídu okna budou založeny na existující třídy, ale použije procedury okna. Tento postup se nazývá vytváření supertříd.  
  
 Kromě použití `DECLARE_WND_CLASS` a `DECLARE_WND_SUPERCLASS` makra, můžete přepsat [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) funkce s vlastní implementaci.  

  
 Další informace o používání oken v ATL, najdete v článku [tříd oken ATL](../../atl/atl-window-classes.md).  
  
##  <a name="declare_wnd_class_ex"></a>DECLARE_WND_CLASS_EX  
 Umožňuje zadat název existující třídy okno na kterém bude na základě novou třídu okna. Třída ovládacích prvků ovládacího prvku ActiveX knihovny ATL umístíte tento makro.  
  
```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```  
  
### <a name="parameters"></a>Parametry  
 `WndClassName`  
 [v] Název třídy pro nové okno. Pokud **NULL**, ATL vygeneruje název třídy oken.  
  
 `style`  
 [v] Styl okna.  
  
 *pozadí –*  
 [v] Barva pozadí okna.  
  
### <a name="remarks"></a>Poznámky  
 Toto makro můžete zadat parametry třída nové třídy oken, jejichž informace bude spravovat [CWndClassInfo](cwndclassinfo-class.md). `DECLARE_WND_CLASS_EX`Definuje novou třídu okno implementací statické následující funkce:  
  
 [!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]  
  
 Pokud chcete použít výchozí styly a barvu pozadí, použijte [DECLARE_WND_CLASS](#declare_wnd_class) makro. Další informace o používání oken v ATL, najdete v článku [tříd oken ATL](../../atl/atl-window-classes.md).  
  
## <a name="see-also"></a>Viz také  
 [Makra](atl-macros.md)









