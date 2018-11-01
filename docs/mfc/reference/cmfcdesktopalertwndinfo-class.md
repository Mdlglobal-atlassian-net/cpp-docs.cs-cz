---
title: Cmfcdesktopalertwndinfo – třída
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
ms.openlocfilehash: d815abbd48e1744900853fcf81dc05b6af62788c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509067"
---
# <a name="cmfcdesktopalertwndinfo-class"></a>Cmfcdesktopalertwndinfo – třída

`CMFCDesktopAlertWndInfo` Třída se používá s [cmfcdesktopalertwnd – třída](../../mfc/reference/cmfcdesktopalertwnd-class.md). Určuje ovládací prvky, které se zobrazí, pokud se otevře okno výstrah plochy.

## <a name="syntax"></a>Syntaxe

```
class CMFCDesktopAlertWndInfo
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo::operator =](#operator_eq)||

### <a name="data-members"></a>Datové členy

|Název|Popis|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)|Popisovač pro ikonu, která se zobrazí.|
|[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)|ID příkazu, který je spojený s odkazem na okno výstrah plochy.|
|[CMFCDesktopAlertWndInfo::m_strText](#m_strtext)|Text, který se zobrazí na okno výstrah plochy.|
|[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)|Odkaz, který se zobrazí na okno výstrah plochy.|

## <a name="remarks"></a>Poznámky

`CMFCDesktopAlertWndInfo` Třídy je předán [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) metodu k určení prvků, které jsou zobrazeny v okně výchozí okno výstrah plochy. Výchozí dialogové okno může obsahovat tři položky:

- Ikona, která je nastavena pomocí volání [CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon).

- Popisek nebo textové zprávy, která je nastavena pomocí volání [CMFCDesktopAlertWndInfo::m_strText](#m_strtext).

- Odkaz, který je nastaven voláním [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl). Chcete-li nastavit příkaz, který se spouští při kliknutí na odkaz, zavolejte [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid).

Pokud výchozí dialogové okno není dostatečná, můžete vytvořit vlastní dialogové okno a předejte jej [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) metoda namísto použití této třídy. Další informace najdete v tématu [cmfcdesktopalertdialog – třída](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak využívat různé členy v `CMFCDesktopAlertWndInfo` třídy. Tento příklad ukazuje, jak nastavit úchyt na ikonu, která se zobrazí text, který se zobrazuje na okno výstrah plochy, na odkaz, který se zobrazí na okno výstrah plochy a ID příkazu, který je spojen s odkazem na okno výstrah plochy. V tomto příkladu je součástí [Desktopu výstrah demonstrační ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Cmfcdesktopalertwndinfo –](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxDesktopAlertDialog.h

##  <a name="operator_eq"></a>  CMFCDesktopAlertWndInfo::operator =

Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

```
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```

### <a name="parameters"></a>Parametry

[in] *src*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="m_hicon"></a>  CMFCDesktopAlertWndInfo::m_hIcon

Popisovač pro ikonu, která se zobrazí.

```
HICON m_hIcon;
```

### <a name="remarks"></a>Poznámky

##  <a name="m_nurlcmdid"></a>  CMFCDesktopAlertWndInfo::m_nURLCmdID

ID příkazu, který je spojený s odkazem na okno výstrah plochy.

```
UINT m_nURLCmdID;
```

### <a name="remarks"></a>Poznámky

ID příkazu, který se odešle vlastníkovi automaticky otevíraném okně, když uživatel klikne na odkaz určený [CMFCDesktopAlertWndInfo::m_strURL](#m_strurl).

##  <a name="m_strtext"></a>  CMFCDesktopAlertWndInfo::m_strText

Text, který se zobrazí na okno výstrah plochy.

```
CString m_strText;
```

### <a name="remarks"></a>Poznámky

##  <a name="m_strurl"></a>  CMFCDesktopAlertWndInfo::m_strURL

Odkaz, který se zobrazí na okno výstrah plochy.

```
CString m_strURL;
```

### <a name="remarks"></a>Poznámky

Když uživatel klikne na odkaz, příkaz, který má [CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid) ID příkazu se pošle vlastníkovi v automaticky otevíraném okně.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd – třída](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)<br/>
[CMFCDesktopAlertDialog – třída](../../mfc/reference/cmfcdesktopalertdialog-class.md)
