---
title: "Nasazení aplikace Visual C++ do složky aplikace local | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: deploying Visual C++ applications
ms.assetid: 47a81c47-9dbe-47c6-96cc-fbb2fda5e6ad
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ba12271fa4614b5ec0c7c70b3a7773152ebfec3c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-deploying-a-visual-c-application-to-an-application-local-folder"></a>Návod: Nasazení aplikace Visual C++ do místní složky aplikace
Popisuje postup nasazení aplikace Visual C++ pomocí kopírování souborů do své složky.  
  
## <a name="prerequisites"></a>Požadavky  
  
-   Počítač, který má nainstalovanou sadu Visual Studio.  
  
-   Jiný počítač, který nemá knihovny jazyka Visual C++.  
  
### <a name="to-deploy-an-application-to-an-application-local-folder"></a>Nasazení aplikace do složky místní aplikace  
  
1.  Vytvořte a sestavte aplikaci MFC podle kroků v [návod: nasazení Visual C++ aplikace pomocí projektu instalace](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).  
  
2.  Zkopírujte příslušné soubory knihovny MFC a C Run-Time (CRT) – například pro x86 platformy a podpora kódování Unicode, kopie mfc100u.dll a msvcr100.dll ze sady Visual Studio 10.0\VC\redist\x86\—and \Program Files\Microsoft vložte je do složky \Release\ projektu knihovny MFC. Další informace o další soubory, které možná budete muset zkopírovat najdete v tématu [určení, které knihovny DLL znovu distribuovat](../ide/determining-which-dlls-to-redistribute.md).  
  
3.  Spusťte aplikaci MFC na druhém počítači, který nemá knihovny jazyka Visual C++.  
  
    1.  Zkopírujte obsah složky \Release\ a vložte je ve složce aplikace v druhém počítači.  
  
    2.  Spuštění aplikace na druhém počítači.  
  
     Aplikace se úspěšně proběhne, protože knihovny jazyka Visual C++ jsou k dispozici ve složce místní aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Příklady nasazení](../ide/deployment-examples.md)