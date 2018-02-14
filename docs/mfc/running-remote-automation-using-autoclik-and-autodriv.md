---
title: "Spuštění vzdálené automatizace s použitím příkazů AUTOCLIK a AUTODRIV | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: AUTOCLIK sample [MFC]
ms.assetid: 8900c0de-8dba-4f0a-8d9e-7db77a1f4f46
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 791655047eaf07732e1e006e8cc3ea8e7dec4727
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="running-remote-automation-using-autoclik-and-autodriv"></a>Spuštění vzdálené automatizace s použitím příkazů AUTOCLIK a AUTODRIV
AUTOCLIK je jednoduchý Automation server ukázkovou aplikaci, která můžete použít jako základ, ze kterého chcete získat další informace o vzdálené automatizace. AUTODRIV je jednoduchou aplikaci klienta automatizace, která řídí AUTOCLIK. Můžete je používat k předvedení vzdálené automatizace.  
  
#### <a name="to-install-autoclikexe-on-two-machines-and-drive-it-using-remote-automation"></a>Chcete-li nainstalovat AUTOCLIK. EXE na dva počítače a jednotky pomocí vzdálené automatizace  
  
1.  Nainstalujte [AUTOCLIK](../visual-cpp-samples.md) ukázkovou aplikaci na vývojovém počítači.  
  
2.  Sestavení AUTOCLIK. SOUBOR EXE.  
  
3.  Spusťte AUTOCLIK. EXE v samostatné dotazování a poté vypněte. To se zaregistrovat jako serveru automatizace.  
  
4.  Zkopírujte AUTOCLIK. EXE ke vzdálenému počítači, spusťte jej a poté vypněte.  
  
5.  Spusťte AUTODRIV. EXE v místním počítači a ověřte, že ji spustili začne AUTOCLIK. SOUBOR EXE. Chcete-li získat další informace o AUTODRIV. EXE, najdete v části [AUTOCLIK](../visual-cpp-samples.md).  
  
6.  Na vzdáleném počítači spusťte AUTMGR32. EXE (Správce automatizace).  
  
7.  Na vzdáleném počítači spusťte RACMGR32. EXE (Správce připojení pro vzdálenou automatizaci).  
  
8.  V vzdálené automatizace připojení správce, vyberte AutoClik.Document z **třídy OLE** seznamu.  
  
9. Vyberte zásadu zabezpečení systému z **klientský přístup** kartě k udělení přístupu klientů k AutoClik.Document.  
  
10. V místním počítači spusťte RACMGR32. EXE a vyberte AutoClik.Document z **třídy OLE** seznamu.  
  
11. Z **připojení k serveru** , zvolte adresa síťového vzdálený počítač a příslušné síťový protokol.  
  
12. Se stále AutoClik.Document vybraným v **třídy OLE** seznam pole, zvolte **vzdáleného** příkaz `Register` nabídky.  
  
13. V místním počítači spusťte AUTODRIV. Soubor EXE nebo ekvivalentní AUTOCLIK. Projektu jazyka Visual Basic klíč k vícenásobné aktivaci, pokud chcete mít v jazyce Visual Basic, nikoli knihovny MFC klienta.  
  
 Ve vzdáleném počítači byste teď měli vidět AUTOCLIK provádění příkazy iniciované z místního klienta.  
  
## <a name="see-also"></a>Viz také  
 [Vzdálená automatizace](../mfc/remote-automation.md)

