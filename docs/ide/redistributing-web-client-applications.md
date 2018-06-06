---
title: Redistribuce klientských webových aplikací | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Web applications [C++], redistributing
- deploying applications [C++], Web applications
- Internet applications [C++], redistributing
- application deployment [C++], Web applications
ms.assetid: fe05988b-dee8-4a46-b381-016b5103a6bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 92bd843b24ee13b3d606ba8bb4f4f1cc265e8e5d
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33323193"
---
# <a name="redistributing-web-client-applications"></a>Redistribuce klientských webových aplikací
Pokud vaše aplikace používá třídy MFC implementaci ovládacího prvku WebBrowser (například `CHtmlView` nebo `CHtmlEditView`), Microsoft 4.0 nebo novější musí alespoň být nainstalovaný Internet Explorer minimálně na cílovém počítači.  
  
 Instalaci nejnovější verze aplikace Internet Explorer taky zajišťuje, že cílový počítač obsahuje nejnovější společné soubory řízení.  
  
 Informace o instalaci minimální součástí aplikace Internet Explorer je k dispozici v následujícím článku znalostní báze Knowledge Base:  
  
-   Q185375, postupy: Vytvoření samostatného EXE instalačního souboru aplikace Internet Explorer ([http://support.microsoft.com/support/kb/articles/q185/3/75.asp](http://support.microsoft.com/support/kb/articles/q185/3/75.asp))  
  
 Články znalostní báze můžete vyhledat v MSDN nebo v [ http://support.microsoft.com ](http://support.microsoft.com).  
  
## <a name="see-also"></a>Viz také  
 [Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)