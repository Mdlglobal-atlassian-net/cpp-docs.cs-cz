---
title: Vytvoření nového vlastního prostředku nebo prostředku dat (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary
dev_langs:
- C++
helpviewer_keywords:
- custom resources [C++]
- data resources [C++]
- resources [C++], creating
ms.assetid: 9918bf96-38fa-43a1-a384-572f95d84950
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6a92e7904b3b42422bebf5a80e0f1b03dd818f86
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314575"
---
# <a name="creating-a-new-custom-or-data-resource-c"></a>Vytvoření nového vlastního prostředku nebo prostředku dat (C++)

Můžete vytvořit nový vlastní nebo datový prostředek tak, že prostředek v samostatném souboru pomocí syntaxe souboru normální prostředku skriptů (.rc) a včetně souboru kliknutím pravým tlačítkem myši na projekt v **Průzkumníka řešení** a kliknete na  **Prostředek zahrnuje** v místní nabídce.

### <a name="to-create-a-new-custom-or-data-resource"></a>Chcete-li vytvořit nový vlastní nebo datový prostředek

1. [Vytvořte soubor .rc](../windows/how-to-create-a-resource-script-file.md) , který obsahuje vlastní nebo datový prostředek.

   Můžete zadat vlastní data v souboru .rc, jako v uvozovkách řetězec zakončený hodnotou null, nebo jako celá čísla ve formátu desítkové, hexadecimální nebo osmičkové soustavě.

2. V **Průzkumníka řešení**, klikněte pravým tlačítkem na souboru .rc v projektu a pak klikněte na tlačítko **prostředek zahrnuje** v místní nabídce.

3. V **směrnice času kompilace** zadejte `#include` příkaz, který poskytuje název souboru, který obsahuje vaše vlastní prostředek. Příklad:

```cpp
    #include mydata.rc
 ```

   Ujistěte se, že syntaxe a pravopisu, co zadáte jsou správné. Obsah **směrnice času kompilace** pole jsou vloženy do souboru skriptu prostředků přesně tak, jak jste je zadali.

4. Klikněte na tlačítko **OK** zaznamenat vaše změny.

Dalším způsobem, jak vytvořit vlastní prostředek se má importovat jako vlastní prostředek externího souboru. Další informace najdete v tématu [import a export prostředků](../windows/how-to-import-and-export-resources.md).

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Binární editor](binary-editor.md)