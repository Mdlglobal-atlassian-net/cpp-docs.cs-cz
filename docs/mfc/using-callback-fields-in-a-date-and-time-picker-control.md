---
title: Použití polí zpětného volání v ovládacím prvku pro výběr data a času
ms.date: 11/04/2016
f1_keywords:
- DTN_FORMATQUERY
- DTN_FORMAT
helpviewer_keywords:
- DateTimePicker control [MFC], callback fields
- callback fields in CDateTimeCtrl class [MFC]
- CDateTimeCtrl class [MFC], callback fields
- CDateTimeCtrl class [MFC], handling DTN_FORMAT and DTN_FORMATQ
- DTN_FORMATQUERY notification [MFC]
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: 404f4ba9-cba7-4718-9faa-bc6b274a723f
ms.openlocfilehash: 50350e51b6747d8c010db9d0dcaa9dff2e56e1f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366560"
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>Použití polí zpětného volání v ovládacím prvku pro výběr data a času

Kromě znaků standardního formátu, které definují pole pro výběr data a času, můžete přizpůsobit výstup zadáním určitých částí vlastního formátovacího řetězce jako polí zpětného volání. Chcete-li deklarovat pole zpětného volání, uveďte jeden nebo více znaků "X" (ASCII Code 88) kdekoli v těle formátovacího řetězce. Například následující řetězec "'Dnes je: 'yy'/'MM'/'dd' (Den 'X')'"způsobí, že ovládací prvek výběru data a času zobrazí aktuální hodnotu jako rok následovaný měsícem, datem a nakonec dnem v roce.

> [!NOTE]
> Počet X v poli zpětného volání neodpovídá počtu znaků, které budou zobrazeny.

Můžete rozlišovat mezi více polí zpětného volání ve vlastním řetězci opakováním znaku "X". Formátovací řetězec "XXddddMMDdd", "yyyXXX" tedy obsahuje dvě jedinečná pole zpětného volání, "XX" a "XXX".

> [!NOTE]
> Pole zpětného volání jsou považována za platná pole, takže aplikace musí být připravena ke zpracování DTN_WMKEYDOWN oznámení.

Implementace polí zpětného volání v ovládacím prvku výběru data a času se skládá ze tří částí:

- Inicializace vlastního formátovacího řetězce

- Zpracování oznámení DTN_FORMATQUERY

- Zpracování DTN_FORMAT oznámení

## <a name="initializing-the-custom-format-string"></a>Inicializace vlastního formátovacího řetězce

Inicializovat vlastní řetězec voláním `CDateTimeCtrl::SetFormat`. Další informace naleznete [v tématu Použití vlastních formátovacích řetězců v ovládacím prvku pro výběr data a času](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md). Běžné místo pro nastavení vlastního formátovacího řetězce je ve `OnInitDialog` `OnInitialUpdate` funkci obsahující třídy dialognebo funkce obsahující třídy zobrazení.

## <a name="handling-the-dtn_formatquery-notification"></a>Zpracování oznámení DTN_FORMATQUERY

Když ovládací prvek analyzuje formátovací řetězec a narazí na pole zpětného volání, aplikace odešle DTN_FORMAT a DTN_FORMATQUERY oznámení. Řetězec pole zpětného volání je součástí oznámení, takže můžete určit, které pole zpětného volání je dotazováno.

Oznámení DTN_FORMATQUERY je odesláno k načtení maximální povolené velikosti v pixelech řetězce, který se zobrazí v aktuálním poli zpětného volání.

Chcete-li správně vypočítat tuto hodnotu, musíte vypočítat výšku a šířku řetězce, který má být nahrazen polem, pomocí písma zobrazení ovládacího prvku. Skutečný výpočet řetězce lze snadno dosáhnout voláním funkce [GetTextExtentPoint32](/windows/win32/api/wingdi/nf-wingdi-gettextextentpoint32w) Win32. Jakmile je určena velikost, předajte hodnotu zpět do aplikace a ukončete funkci obslužné rutiny.

Následující příklad je jednou z metod poskytování velikosti řetězce zpětného volání:

[!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]

Po výpočtu velikosti aktuálního pole zpětného volání je nutné zadat hodnotu pole. To se provádí v obslužné rutině pro oznámení DTN_FORMAT.

## <a name="handling-the-dtn_format-notification"></a>Zpracování oznámení DTN_FORMAT

Oznámení DTN_FORMAT používá aplikace k vyžádání řetězce znaků, který bude nahrazen. Následující příklad ukazuje jednu možnou metodu:

[!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]

> [!NOTE]
> Ukazatel na strukturu **NMDATETIMEFORMAT** je nalezen přetypováníprvní parametr obslužné rutiny oznámení na správný typ.

## <a name="see-also"></a>Viz také

[Používání atributu CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
