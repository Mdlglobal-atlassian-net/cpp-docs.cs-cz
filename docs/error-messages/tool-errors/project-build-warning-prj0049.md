---
title: Projekt sestavení PRJ0049 upozornění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 169ba63318f630ac6a63b18d34fd6a7d829f4f90
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110884"
---
# <a name="project-build-warning-prj0049"></a>Upozornění sestavení projektu PRJ0049

Odkazovaný cíl "\<odkaz > se vyžaduje rozhraní .NET Framework \<MinFrameworkVersion > a nebude schopen provést spuštění na cílovém rozhraní projektu.

Aplikace vytvořené pomocí sady Visual Studio 2008 můžete určit, kterou verzi rozhraní .NET Framework by měl cílí. Pokud chcete přidat odkaz na sestavení nebo projekt, který závisí na verzi rozhraní .NET Framework, která je vyšší než cílová verze, zobrazí se toto upozornění v době kompilace.

### <a name="to-correct-this-warning"></a>Chcete-li opravit toto upozornění

1. Vyberte jednu z následujících možností:

   - Změnit cílová rozhraní framework v projektu **stránky vlastností** dialogové okno tak, aby se novější než nebo rovna hodnotě minimální framework verze projektů a všemi odkazovanými sestaveními. Další informace najdete v tématu [přidávání odkazů na](../../ide/adding-references-in-visual-cpp-projects.md).

   - Odeberte odkaz na sestavení nebo projekt, který má minimální framework verzi, která je novější než cíleného rozhraní. Tyto položky budou označeny ikonou upozornění v projektu **stránky vlastností**.

## <a name="see-also"></a>Viz také

[Chyby a upozornění sestavení projektu (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)