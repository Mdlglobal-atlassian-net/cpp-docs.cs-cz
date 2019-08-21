---
title: Požadavky na sestavení pro běžné ovládací prvky systému Windows
ms.date: 08/19/2019
helpviewer_keywords:
- Common Controls (MFC), build requirements
- Common Controls (MFC)
ms.assetid: 025f7d55-55a2-4dcd-8f62-02424e3dcc04
ms.openlocfilehash: 9ea90f95ba8e704cba5b22c5e7338659f0c5f033
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630848"
---
# <a name="build-requirements-for-windows-common-controls"></a>Požadavky na sestavení pro běžné ovládací prvky systému Windows

Knihovna Microsoft Foundation Class (MFC) podporuje [běžné ovládací prvky systému Windows](/windows/win32/controls/common-controls-intro). Společné ovládací prvky jsou součástí systému Windows a knihovna je součástí sady Visual Studio. Knihovna MFC poskytuje nové metody, které vylepšují existující třídy, a další třídy a metody, které podporují běžné ovládací prvky systému Windows. Při sestavování aplikace byste měli postupovat podle požadavků kompilace a migrace, které jsou popsány v následujících částech.

## <a name="compilation-requirements"></a>Požadavky na kompilaci

### <a name="supported-versions"></a>Podporované verze

Knihovna MFC podporuje všechny verze běžných ovládacích prvků. Informace o verzích běžných ovládacích prvků systému Windows naleznete v tématu [Common Control Versions](/windows/win32/controls/common-control-versions).

### <a name="supported-character-sets"></a>Podporované znakové sady

Běžné ovládací prvky systému Windows podporují pouze znakovou sadu Unicode, nikoli znakovou sadu ANSI. Pokud sestavíte aplikaci na příkazovém řádku, použijte obě z následujících možností kompilátoru define (/D) k zadání kódu Unicode jako základní znakové sady:

```
/D_UNICODE /DUNICODE
```

Pokud sestavíte aplikaci v integrovaném vývojovém prostředí (IDE) sady Visual Studio, zadejte možnost **znakové sady Unicode** vlastnosti **znaková sada** v uzlu **Obecné** vlastností projektu.

## <a name="migration-requirements"></a>Požadavky na migraci

Použijete-li rozhraní IDE sady Visual Studio k sestavení nové aplikace MFC, která používá běžné ovládací prvky systému Windows, rozhraní IDE automaticky deklaruje příslušný manifest. Pokud však migrujete existující aplikaci knihovny MFC ze sady Visual Studio 2005 nebo starší a chcete použít běžné ovládací prvky, rozhraní IDE automaticky neposkytne informace o manifestu pro upgrade vaší aplikace. Místo toho je nutné ručně vložit následující zdrojový kód do souboru předkompilované hlavičky:

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

## <a name="see-also"></a>Viz také:

[Obecná témata MFC](../mfc/general-mfc-topics.md)<br/>
[Graf hierarchie](../mfc/hierarchy-chart.md)<br/>
[Zastaralá rozhraní API standardu ANSI](../mfc/deprecated-ansi-apis.md)
