---
title: Nastavení aplikace, Průvodce MFC DLL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.dll.appset
dev_langs:
- C++
helpviewer_keywords:
- MFC DLL Wizard, application settings
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a243b790881452a983c43fb92d8ebea18c26bcc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="application-settings-mfc-dll-wizard"></a>Nastavení aplikace, průvodce MFC DLL
Na této stránce Průvodce MFC DLL návrh a přidat základní funkce do nového projektu knihovny MFC DLL.  
  
## <a name="dll-type"></a>Typ knihovny DLL  
 Vyberte typ knihovny DLL, kterou chcete vytvořit.  
  
 **Regulární knihovny MFC DLL pomocí sdílené knihovně MFC DLL**  
 Vyberte tuto možnost propojení knihovny MFC s vaším programem jako sdílenou knihovnu DLL. Použití této možnosti nelze sdílet objekty MFC mezi knihovnou DLL a volající aplikace. Program volá knihovny MFC za běhu. Tato možnost snižuje požadavky na disk a paměť vašeho programu, pokud se skládá z několika provádění soubory, které používají knihovny MFC. Win32 a MFC programy můžete volat funkce v knihovně DLL. Je třeba znovu distribuovat MFC DLL s tímto typem projektu.  
  
 **Staticky propojené běžné knihovny MFC DLL s knihovnou MFC**  
 Tuto možnost propojit váš program staticky knihovny MFC v čase vytvoření buildu. Win32 a MFC programy můžete volat funkce v knihovně DLL. Když tuto možnost zvyšuje velikost vašeho programu, není potřeba znovu distribuovat MFC DLL s tímto typem projektu. MFC – objekty nemohou sdílet mezi knihovnou DLL a volající aplikace.  
  
 **MFC – rozšiřující knihovny DLL**  
 Tuto možnost vyberte, pokud chcete, aby váš program pro volání do knihovny MFC za běhu, a pokud chcete sdílet objekty knihovny MFC mezi knihovnou DLL a volající aplikace. Tato možnost snižuje požadavky na disk a paměť vašeho programu, pokud se skládá z několika spustitelné soubory, které využívají knihovny MFC. Pouze MFC programy můžete volat funkce v knihovně DLL. Je třeba znovu distribuovat MFC DLL s tímto typem projektu.  
  
## <a name="additional-features"></a>Další funkce  
 Vyberte, zda vaše knihovna MFC DLL musí podporovat automatizace a zda má podporovat rozhraní Windows sockets.  
  
 **Automatizace**  
 Vyberte **automatizace** umožnit programu manipulovat s objekty, které jsou implementované v jiném programu. Výběr **automatizace** také poskytuje váš program jiným klientům automatizace. V tématu [automatizace](../../mfc/automation.md) Další informace.  
  
 **Windows sockets**  
 Vyberte tuto možnost určíte, že daná aplikace podporuje rozhraní Windows sockets. Windows sockets umožňují psát programy, které komunikují přes sítích TCP/IP.  
  
 Když Knihovnu MFC s Windows sockets podpory se vytvoří, [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) inicializuje podpora pro sokety a hlavičkový soubor knihovny MFC StdAfx.h AfxSock.h.  
  
## <a name="see-also"></a>Viz také  
 [MFC DLL – Průvodce knihovnou](../../mfc/reference/mfc-dll-wizard.md)   
 [Vytvoření projektu knihovny MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md)

