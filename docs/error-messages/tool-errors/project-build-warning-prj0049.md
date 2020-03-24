---
title: Upozornění sestavení projektu PRJ0049
ms.date: 11/04/2016
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
ms.openlocfilehash: e857a50215dc7516c0e2ec45a97638c76f40f43b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191743"
---
# <a name="project-build-warning-prj0049"></a>Upozornění sestavení projektu PRJ0049

Odkazovaný cíl '\<reference > ' vyžaduje .NET Framework \<MinFrameworkVersion > a nebude možné ho spustit v cílovém rozhraní .NET Framework tohoto projektu

Aplikace vytvořené pomocí sady Visual Studio 2008 mohou určit, která verze .NET Framework mají cílit. Pokud přidáte odkaz na sestavení nebo projekt, který závisí na verzi .NET Framework, která je novější než cílová verze, zobrazí se toto upozornění v době kompilace.

### <a name="to-correct-this-warning"></a>Chcete-li toto upozornění opravit

1. Vyberte jednu z následujících možností:

   - V dialogovém okně **stránky vlastností** projektu změňte cílové rozhraní tak, aby bylo pozdější než nebo rovno verzi minimálního rozhraní všech odkazovaných sestavení a projektů. Další informace najdete v tématu [Přidání odkazů](../../build/adding-references-in-visual-cpp-projects.md).

   - Odeberte odkaz na sestavení nebo projekt s minimální verzí rozhraní, která je novější než cílové rozhraní. Tyto položky budou označeny ikonou upozornění na **stránkách vlastností**projektu.

## <a name="see-also"></a>Viz také

[Chyby a upozornění sestavení projektu (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
