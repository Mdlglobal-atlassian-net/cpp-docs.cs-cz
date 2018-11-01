---
title: Upozornění sestavení projektu PRJ0049
ms.date: 11/04/2016
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
ms.openlocfilehash: a451b7fe7b2f7cd89f8898232badf0d3b7e9f138
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447213"
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