---
title: CMFCDesktopAlertWndInfo – třída
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_hIcon
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_nURLCmdID
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strText
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strURL
helpviewer_keywords:
- CMFCDesktopAlertWndInfo [MFC], m_hIcon
- CMFCDesktopAlertWndInfo [MFC], m_nURLCmdID
- CMFCDesktopAlertWndInfo [MFC], m_strText
- CMFCDesktopAlertWndInfo [MFC], m_strURL
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
ms.openlocfilehash: f51c1b75e0c096a34b190e36e097aaca4109b5f8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367589"
---
# <a name="cmfcdesktopalertwndinfo-class"></a>CMFCDesktopAlertWndInfo – třída

Třída `CMFCDesktopAlertWndInfo` se používá s [TŘÍDOU CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md). Určuje ovládací prvky, které se zobrazí, pokud se objeví okno výstrahy plochy.

## <a name="syntax"></a>Syntaxe

```
class CMFCDesktopAlertWndInfo
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo::operátor=](#operator_eq)||

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)|Úchyt k zobrazené ikoně.|
|[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)|ID příkazu přidružené k odkazu v okně upozornění na ploše.|
|[CMFCDesktopAlertWndInfo::m_strText](#m_strtext)|Text, který se zobrazí v okně výstrahy plochy.|
|[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)|Odkaz, který se zobrazí v okně výstrahy plochy.|

## <a name="remarks"></a>Poznámky

Třída `CMFCDesktopAlertWndInfo` je předána [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) metoda určit prvky, které jsou zobrazeny na výchozí dialogové okno plochy výstražného okna. Výchozí dialogové okno může obsahovat tři položky:

- Ikona, která je nastavena voláním [CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon).

- Popisek nebo textová zpráva, která je nastavena voláním [CMFCDesktopAlertWndInfo::m_strText](#m_strtext).

- Odkaz, který je nastaven voláním [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl). Chcete-li nastavit příkaz, který je proveden po klepnutí na odkaz, zavolejte [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid).

Pokud výchozí dialogové okno není dostačující, můžete vytvořit vlastní dialogové okno a předat jej [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) metoda namísto použití této třídy. Další informace naleznete v tématu [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCDesktopAlertWndInfo` členy ve třídě. Příklad ukazuje, jak nastavit popisovač na ikonu, která je zobrazena, text, který se zobrazí v okně upozornění plochy, odkaz, který se zobrazí v okně upozornění plochy a ID příkazu, který je spojen s odkazem na ploše výstražného okna. Tento příklad je součástí [ukázky ukázky upozornění na ploše](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxDesktopAlertDialog.h

## <a name="cmfcdesktopalertwndinfooperator"></a><a name="operator_eq"></a>CMFCDesktopAlertWndInfo::operátor=

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```

### <a name="parameters"></a>Parametry

[v] *src*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcdesktopalertwndinfom_hicon"></a><a name="m_hicon"></a>CMFCDesktopAlertWndInfo::m_hIcon

Úchyt k zobrazené ikoně.

```
HICON m_hIcon;
```

### <a name="remarks"></a>Poznámky

## <a name="cmfcdesktopalertwndinfom_nurlcmdid"></a><a name="m_nurlcmdid"></a>CMFCDesktopAlertWndInfo::m_nURLCmdID

ID příkazu přidružené k odkazu v okně upozornění na ploše.

```
UINT m_nURLCmdID;
```

### <a name="remarks"></a>Poznámky

ID příkazu je odesláno vlastníkovi vyskakovacího okna, když uživatel klikne na odkaz určený [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl).

## <a name="cmfcdesktopalertwndinfom_strtext"></a><a name="m_strtext"></a>CMFCDesktopAlertWndInfo::m_strText

Text, který se zobrazí v okně výstrahy plochy.

```
CString m_strText;
```

### <a name="remarks"></a>Poznámky

## <a name="cmfcdesktopalertwndinfom_strurl"></a><a name="m_strurl"></a>CMFCDesktopAlertWndInfo::m_strURL

Odkaz, který se zobrazí v okně výstrahy plochy.

```
CString m_strURL;
```

### <a name="remarks"></a>Poznámky

Když uživatel klepne na odkaz, příkaz, který má ID příkazu [CMFCDesktopAlertWndInfo::m_nURLCmdID,](#m_nurlcmdid) bude odeslán vlastníkovi rozbalovacího okna.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd – třída](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFCDesktopAlertWnd::Vytvořit](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)<br/>
[Třída CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)
