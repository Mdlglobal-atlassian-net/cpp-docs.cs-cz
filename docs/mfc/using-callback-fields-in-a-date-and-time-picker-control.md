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
ms.openlocfilehash: 5d08c349253e62c15553cfa0452cee930b1a1876
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513505"
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>Použití polí zpětného volání v ovládacím prvku pro výběr data a času

Kromě standardních formátovacích znaků, které definují pole pro výběr data a času, můžete přizpůsobit výstup zadáním určitých částí vlastního formátu řetězce jako pole zpětného volání. Chcete-li deklarovat pole zpětného volání, zahrňte jeden nebo více znaků "X" (kód ASCII 88) kdekoli v těle formátovacího řetězce. Například následující řetězec "' dnes je: ' YY '/' MM '/' DD ' (den ' X ') ' ' způsobí, že ovládací prvek pro výběr data a času zobrazí aktuální hodnotu jako rok následovaný měsíc, datum a nakonec den v roce.

> [!NOTE]
>  Počet X v poli zpětného volání neodpovídá počtu znaků, které se zobrazí.

Můžete rozlišovat mezi více poli zpětného volání ve vlastním řetězci opakováním znaku "X". Proto formátovací řetězec "XXddddMMMdd", "yyyXXX" obsahuje dvě jedinečná pole zpětného volání "XX" a "XXX".

> [!NOTE]
>  Pole zpětného volání se považují za platná pole, takže vaše aplikace musí být připravená na zpracování zpráv s oznámením DTN_WMKEYDOWN.

Implementování polí zpětného volání v ovládacím prvku pro výběr data a času se skládá ze tří částí:

- Inicializuje se řetězec vlastního formátu.

- Zpracování oznámení DTN_FORMATQUERY

- Zpracování oznámení DTN_FORMAT

## <a name="initializing-the-custom-format-string"></a>Inicializuje se řetězec vlastního formátu.

Inicializujte vlastní řetězec voláním metody `CDateTimeCtrl::SetFormat`. Další informace naleznete v tématu [použití vlastních formátovacích řetězců v ovládacím prvku pro výběr data a času](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md). Běžným místem pro nastavení vlastního formátovacího řetězce je `OnInitDialog` funkce, která obsahuje třídu nebo `OnInitialUpdate` funkci obsahující třídu zobrazení.

## <a name="handling-the-dtn_formatquery-notification"></a>Zpracování oznámení DTN_FORMATQUERY

Když ovládací prvek analyzuje řetězec formátu a narazí na pole zpětného volání, aplikace pošle oznamovací zprávy DTN_FORMAT a DTN_FORMATQUERY. Řetězec pole zpětného volání je součástí oznámení, abyste mohli určit, které pole zpětného volání se dotazuje.

Oznámení DTN_FORMATQUERY se pošle, aby se získala maximální povolená velikost v pixelech řetězce, který se zobrazí v aktuálním poli zpětného volání.

Chcete-li tuto hodnotu správně vypočítat, je nutné vypočítat výšku a šířku řetězce, aby bylo možné nahradit pole pomocí písma zobrazení ovládacího prvku. Skutečný výpočet řetězce lze snadno dosáhnout voláním funkce [GetTextExtentPoint32](/windows/win32/api/wingdi/nf-wingdi-gettextextentpoint32w) Win32. Jakmile je velikost určena, předejte hodnotu zpět do aplikace a ukončete funkci obslužné rutiny.

Následující příklad představuje jednu z metod poskytnutí velikosti řetězce zpětného volání:

[!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]

Jakmile je vypočtena velikost aktuálního pole zpětného volání, je nutné pro pole dodat hodnotu. To se provádí v obslužné rutině oznámení DTN_FORMAT.

## <a name="handling-the-dtn_format-notification"></a>Zpracování oznámení DTN_FORMAT

Oznámení DTN_FORMAT používá aplikace k vyžádání řetězce znaků, který bude nahrazen. Následující příklad ukazuje jednu možnou metodu:

[!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]

> [!NOTE]
>  Ukazatel na strukturu **NMDATETIMEFORMAT** je nalezen přetypováním prvního parametru obslužné rutiny oznámení na správný typ.

## <a name="see-also"></a>Viz také:

[Používání atributu CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
