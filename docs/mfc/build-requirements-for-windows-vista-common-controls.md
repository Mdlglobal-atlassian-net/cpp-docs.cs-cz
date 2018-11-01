---
title: Požadavky na sestavení pro běžné ovládací prvky systému Windows Vista
ms.date: 11/04/2016
helpviewer_keywords:
- common controls (MFC), build requirements
- common controls (MFC)
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
ms.openlocfilehash: c9a01665339c28b58a5d528cbb9dfaa235e7f1ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637070"
---
# <a name="build-requirements-for-windows-vista-common-controls"></a>Požadavky na sestavení pro běžné ovládací prvky systému Windows Vista

Knihovny Microsoft Foundation Class (MFC) podporuje běžných ovládacích prvků Windows verze 6.1. Běžné ovládací prvky jsou zahrnuty v systému Windows Vista a knihovny je součástí sady Visual Studio SDK. Knihovna poskytuje nové metody, které rozšiřují existující třídy a nové třídy a metody, které podporují běžné ovládací prvky Windows Vista. Když vytváříte aplikaci, postupujte podle kompilace a migrace požadavky, které jsou popsány v následujících částech.

## <a name="compilation-requirements"></a>Kompilace požadavky

### <a name="supported-versions"></a>Podporované verze

Některé nové třídy a metody podporují pouze Windows Vista a novější, zatímco jiné metody také podporují starší operační systémy. Poznámka: v `Requirements` každého tématu metoda určuje, kdy minimální požadovaný operační systém je Windows Vista.

I v případě, že počítač není spuštěn Windows Vista, můžete vytvářet aplikace knihovny MFC, který se spustí v systému Windows Vista, pokud máte souborech hlaviček knihovny MFC verze 6.1 ve vašem počítači. Běžné ovládací prvky, které jsou určené konkrétně pro Windows Vista však pracovat pouze v daném systému a jsou ignorovány ve starších operačních systémech.

### <a name="supported-character-sets"></a>Podporované znakové sady

Nové běžné ovládací prvky Windows podporují pouze znakové sady Unicode a ne znakovou sadu ANSI. Pokud vytváříte aplikaci na příkazovém řádku, použijte obě následující definovat (/ D) – možnosti kompilátoru k určení kódování Unicode jako základní znakové sady:

```
/D_UNICODE /DUNICODE
```

Pokud vytváříte aplikaci v sadě Visual Studio integrované vývojové prostředí (IDE), zadejte **znakové sady Unicode** možnost **znaková sada** vlastnost **obecné**  uzel vlastností projektu.

ANSI verze z několika metod MFC jsou zastaralé od verze 6.1 běžných ovládacích prvků Windows. Další informace najdete v tématu [zastaralé rozhraní API standardu ANSI](../mfc/deprecated-ansi-apis.md).

## <a name="migration-requirements"></a>Požadavky na migraci

Pokud používáte rozhraní IDE sady Visual Studio k vytvoření nové aplikace knihovny MFC, která používá běžné ovládací prvky Windows verze 6.1, rozhraní IDE automaticky deklaruje odpovídající manifestu. Nicméně pokud migrujete existující aplikaci MFC ze starší verze sady Visual Studio a chcete použít nové běžné ovládací prvky, rozhraní IDE neposkytuje automaticky informace o manifestu k upgradu vaší aplikace. Místo toho je nutné ručně vložit následující zdrojový kód v vaše **stdafx.h** souboru:

```
#ifdef UNICODE
#if defined _M_IX86
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='x86' publicKeyToken='6595b64144ccf1df' language='*'\"")
#elif defined _M_IA64
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='ia64' publicKeyToken='6595b64144ccf1df' language='*'\"")
#elif defined _M_X64
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='amd64' publicKeyToken='6595b64144ccf1df' language='*'\"")
#else
#pragma comment(linker,"/manifestdependency:\"type='win32' name='Microsoft.Windows.Common-Controls' version='6.0.0.0' processorArchitecture='*' publicKeyToken='6595b64144ccf1df' language='*'\"")
#endif
#endif
```

## <a name="see-also"></a>Viz také

[Obecná témata MFC](../mfc/general-mfc-topics.md)<br/>
[Graf hierarchie](../mfc/hierarchy-chart.md)<br/>
[Zastaralá rozhraní API standardu ANSI](../mfc/deprecated-ansi-apis.md)

