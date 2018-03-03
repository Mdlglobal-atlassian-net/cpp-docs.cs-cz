---
title: "Redistribuce klientských webových aplikací | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Web applications [C++], redistributing
- deploying applications [C++], Web applications
- Internet applications [C++], redistributing
- application deployment [C++], Web applications
ms.assetid: fe05988b-dee8-4a46-b381-016b5103a6bf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e764e42cb558d2e13e0609cb139e9538a72d09ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="redistributing-web-client-applications"></a>Redistribuce klientských webových aplikací
Pokud vaše aplikace používá třídy MFC implementaci ovládacího prvku WebBrowser (například `CHtmlView` nebo `CHtmlEditView`), Microsoft 4.0 nebo novější musí alespoň být nainstalovaný Internet Explorer minimálně na cílovém počítači.  
  
 Instalaci nejnovější verze aplikace Internet Explorer taky zajišťuje, že cílový počítač obsahuje nejnovější společné soubory řízení.  
  
 Informace o instalaci minimální součástí aplikace Internet Explorer je k dispozici v následujícím článku znalostní báze Knowledge Base:  
  
-   Q185375, postupy: Vytvoření samostatného EXE instalačního souboru aplikace Internet Explorer ([http://support.microsoft.com/support/kb/articles/q185/3/75.asp](http://support.microsoft.com/support/kb/articles/q185/3/75.asp))  
  
 Články znalostní báze můžete vyhledat v MSDN nebo v [http://support.microsoft.com](http://support.microsoft.com).  
  
## <a name="see-also"></a>Viz také  
 [Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)