---
title: 'Schránka: Použití mechanismu schránky OLE'
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard
- Clipboard [MFC], OLE formats
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
ms.openlocfilehash: 0f2c10f4a88b723d1ab9f4bb0ca903987359c9fd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508905"
---
# <a name="clipboard-using-the-ole-clipboard-mechanism"></a>Schránka: Použití mechanismu schránky OLE

Technologie OLE používá pro přenos dat prostřednictvím schránky standardní formáty a některé formáty specifické pro OLE.

Při vyjmutí nebo zkopírování dat z aplikace jsou data uložena ve schránce pro pozdější použití v rámci operací vložení. Tato data jsou v nejrůznějších formátech. Když se uživatel rozhodne vkládat data ze schránky, aplikace může zvolit, který z těchto formátů se má použít. Aplikace by měla být zapsána pro výběr formátu, který poskytuje nejvíc informací, pokud se uživatel výslovně nezeptá na určitý formát, a to pomocí příkazu Vložit jinak. Než budete pokračovat, možná budete chtít přečíst témata [datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md) . Popisují základy přenosu dat a způsob jejich implementace ve vašich aplikacích.

Systém Windows definuje počet standardních formátů, které lze použít k přenosu dat ze schránky. Mezi ně patří metasoubory, text, bitmapy a další. OLE definuje také více formátů specifických pro OLE. Pro aplikace, které vyžadují více podrobností než tyto standardní formáty, je vhodné registrovat vlastní formáty schránky. K tomu použijte funkci Win32 API [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) .

Například Microsoft Excel registruje vlastní formát pro tabulky. Tento formát přináší mnohem více informací, než například rastrový obrázek. Když se tato data vloží do aplikace podporující formát tabulky, všechny vzorce a hodnoty z tabulky se zachovají a v případě potřeby je můžete aktualizovat. Aplikace Microsoft Excel také vloží data ze schránky do formátu tak, aby mohla být vložena jako položka OLE. Libovolný kontejner dokumentů OLE může vložit tyto informace jako vloženou položku. Tuto vloženou položku lze změnit pomocí aplikace Microsoft Excel. Schránka obsahuje také jednoduchý rastrový obrázek obrázku vybraného rozsahu v tabulce. To lze také vložit do kontejnerů dokumentů OLE nebo do editorů rastrových obrázků, jako je například Malování. V případě rastrového obrázku však neexistuje způsob, jak manipulovat s daty jako s tabulkou.

Chcete-li načíst maximální množství informací ze schránky, aplikace by měly před vložením dat ze schránky vyhledat tyto vlastní formáty.

Chcete-li například povolit příkaz Vyjmout, můžete napsat obslužnou rutinu podobný následujícímu:

[!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace

- [Kopírování a vkládání dat](../mfc/clipboard-copying-and-pasting-data.md)

- [Přidávání dalších formátů](../mfc/clipboard-adding-other-formats.md)

- [Použití schránky systému Windows](../mfc/clipboard-using-the-windows-clipboard.md)

- [OBJEKTŮ](../mfc/ole-background.md)

- [Datové objekty OLE a zdroje dat a jednotný přenos dat](../mfc/data-objects-and-data-sources-ole.md)

## <a name="see-also"></a>Viz také:

[Schránka](../mfc/clipboard.md)
