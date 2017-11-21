---
title: "Co je ATL – hostování ovládacího prvku rozhraní API? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- APIs [C++], hosting
- control-hosting API
- controls [ATL], hosting APIs
ms.assetid: 75b27e45-cfba-4950-aa35-96cc7d8da753
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4f04f5caa30ab860634f0f96ae18e9da03577ba2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="what-is-the-atl-control-hosting-api"></a>Co je ATL – hostování ovládacího prvku rozhraní API?
Je ATL – hostování ovládacího prvku rozhraní API je sada funkcí, která umožňuje všechny okna tak, aby fungoval jako kontejneru ovládacího prvku ActiveX. Tyto funkce můžou být staticky nebo dynamicky propojené do projektu, protože jsou k dispozici jako zdrojový kód a vystavené ATL90.dll. V následující tabulce jsou uvedené funkce hostování ovládacího prvku.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|Vytvoří objekt hostitele, připojí k zadané okna a potom připojí existujícího ovládacího prvku.|  
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Vytvoří objekt hostitele, připojí k zadané okna a pak načte ovládacího prvku.|  
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Vytvoří licencované ovládací prvek ActiveX, inicializuje ji a hostuje v zadané okno podobné [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol).|  
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Vytvoří objekt hostitele, připojí k zadané okna a potom načte ovládacího prvku (také umožní navázání jímky událostí).|  
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Vytvoří licencované ovládací prvek ActiveX, inicializuje ji a hostuje v zadané okno podobné [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic).|  
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Vytvoří dialogové okno nemodální z prostředku dialogového okna a vrátí popisovač okna.|  
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|Vytvoří modální dialogové okno z prostředku dialogového okna.|  
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Vrátí **IUnknown** ukazatel rozhraní ovládacího prvku hostované v okně.|  
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|Vrátí **IUnknown** ukazatel rozhraní objektu hostitele připojené k časového období.|  
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|Inicializuje kód hostování ovládacího prvku.|  
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|Uninitializes kód hostování ovládacího prvku.|  
  
 `HWND` Parametry v první tři funkce musí být existujícího okna (téměř) libovolného typu. Pokud některý z těchto tří funkcí explicitně zavoláte (obvykle, nebudete muset), nepředávejte popisovač okna, které již funguje jako hostitele (v takovém případě je existující objekt hostitele neuvolní).  
  
 Volání funkce nejprve sedm [AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) implicitně.  
  
> [!NOTE]
>  Rozhraní API hostování ovládacího prvku tvoří základ pro ATL – podpora pro uzavření ovládacího prvku ActiveX. Je však obvykle moc potřeba přímo volat tyto funkce v případě, že můžete využít výhod nebo plně využít obálkové třídy ATL společnosti. Další informace najdete v tématu [který ATL třídy usnadnění ActiveX uzavření ovládacího prvku](which-atl-classes-facilitate-activex-control-containment-q.md).  
  
## <a name="see-also"></a>Viz také  
 [Uzavření ovládacího prvku – nejčastější dotazy](which-atl-classes-facilitate-activex-control-containment-q.md)
