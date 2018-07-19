---
title: Co je knihovny ATL – hostování ovládacího prvku rozhraní API? | Dokumenty Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- APIs [C++], hosting
- control-hosting API
- controls [ATL], hosting APIs
ms.assetid: 75b27e45-cfba-4950-aa35-96cc7d8da753
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2cc85c7ca47d5d1226ffc3089e01c0755ef6c6ac
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37850550"
---
# <a name="what-is-the-atl-control-hosting-api"></a>Co je knihovny ATL – hostování ovládacího prvku rozhraní API?
V ATL – hostování ovládacího prvku rozhraní API je sada funkcí, které umožňuje jakékoli okno tak, aby fungoval jako kontejneru ovládacího prvku ActiveX. Tyto funkce může být staticky nebo dynamicky propojené do vašeho projektu, protože jsou k dispozici jako zdrojový kód a vystavené ATL90.dll. V následující tabulce jsou uvedeny funkce hostování ovládacího prvku.  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|Vytvoří objekt hostitele, připojí k zadané okno a potom připojí existujícího ovládacího prvku.|  
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Vytvoří objekt hostitele, připojí k zadané okna a pak načte ovládací prvek.|  
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Vytvoří licencovaného ovládacího prvku ActiveX, inicializuje ji a hostuje ji v zadaném okně, podobně jako [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol).|  
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Vytvoří objekt hostitele, připojí k zadané okna a pak načte ovládací prvek (také umožní navázání jímky událostí).|  
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Vytvoří licencovaného ovládacího prvku ActiveX, inicializuje ji a hostuje ji v zadaném okně, podobně jako [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic).|  
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Vytvoří nemodální dialogové okno z prostředku dialogového okna a vrátí popisovač okna.|  
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|Vytvoří modální dialogové okno z prostředku dialogového okna.|  
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Vrátí `IUnknown` ukazatel rozhraní ovládací prvek je hostován v okně.|  
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|Vrátí `IUnknown` ukazatel rozhraní objektu hostitel připojený k časového období.|  
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|Inicializuje kód hostování ovládacího prvku.|  
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|Zruší inicializaci kód hostování ovládacího prvku.|  
  
 `HWND` Parametry v první tři funkce musí být existujícímu oknu (téměř) libovolného typu. Pokud některý z těchto tří funkcí můžete explicitně volat (obvykle není nutné), nepředávejte popisovač okna, která už funguje jako hostitele (Pokud ano, existující hostitelský objekt se neuvolní).  
  
 Nejprve sedm funkce volání [AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) implicitně.  
  
> [!NOTE]
>  Rozhraní API pro hostování ovládacího prvku tvoří základ pro podporu ATL pro používání kontejnerů ovládacích prvků ActiveX. Však není obvykle nutné volat tyto funkce přímo-li využít výhod nebo vytěžíte ATL obálkové třídy. Další informace najdete v tématu [která ATL – třídy usnadnění ActiveX používání kontejnerů ovládacích prvků](which-atl-classes-facilitate-activex-control-containment-q.md).  
  
## <a name="see-also"></a>Viz také  
 [Nejčastější dotazy k používání kontejnerů ovládacích prvků](which-atl-classes-facilitate-activex-control-containment-q.md)
