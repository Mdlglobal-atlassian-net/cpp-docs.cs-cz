---
title: "PRJ0049 upozornění sestavení projektu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f87bc7e26fd7cc50defbc086594c92a3ea339ef
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-warning-prj0049"></a>Upozornění sestavení projektu PRJ0049
Odkazovaná cíl '\<odkaz > se vyžaduje rozhraní .NET Framework \<MinFrameworkVersion > a nebude možné spustit na cílový framework projektu na  
  
 Aplikace vytvořené pomocí sady Visual Studio 2008, můžete určit používanou verzi [!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)] budou cílem by měl. Pokud přidáte odkaz na sestavení nebo projekt, který závisí na verzi [!INCLUDE[dnprdnshort](../../error-messages/tool-errors/includes/dnprdnshort_md.md)] , je novější než cílová verze, zobrazí se toto upozornění při kompilaci.  
  
### <a name="to-correct-this-warning"></a>Chcete-li toto upozornění  
  
1.  Vyberte jednu z následujících možností:  
  
    -   Změňte cílový framework v projektu **stránky vlastností** dialogu tak, aby se později než nebo rovna minimální framework verze všechny odkazované sestavení a projekty. Další informace najdete v tématu [přidávání odkazů](../../ide/adding-references-in-visual-cpp-projects.md).  
  
    -   Odeberte odkaz na sestavení nebo projekt, který má minimální framework verzi, která je novější než cílové rozhraní. Tyto položky budou označeny ikonou upozornění v projektu **stránky vlastností**.  
  
## <a name="see-also"></a>Viz také  
 [Chyby a upozornění sestavení projektu (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)