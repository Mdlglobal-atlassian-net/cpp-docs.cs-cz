---
title: Třída COleChangeSourceDialog | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::COleChangeSourceDialog
- AFXODLGS/COleChangeSourceDialog::DoModal
- AFXODLGS/COleChangeSourceDialog::GetDisplayName
- AFXODLGS/COleChangeSourceDialog::GetFileName
- AFXODLGS/COleChangeSourceDialog::GetFromPrefix
- AFXODLGS/COleChangeSourceDialog::GetItemName
- AFXODLGS/COleChangeSourceDialog::GetToPrefix
- AFXODLGS/COleChangeSourceDialog::IsValidSource
- AFXODLGS/COleChangeSourceDialog::m_cs
dev_langs:
- C++
helpviewer_keywords:
- COleChangeSourceDialog [MFC], COleChangeSourceDialog
- COleChangeSourceDialog [MFC], DoModal
- COleChangeSourceDialog [MFC], GetDisplayName
- COleChangeSourceDialog [MFC], GetFileName
- COleChangeSourceDialog [MFC], GetFromPrefix
- COleChangeSourceDialog [MFC], GetItemName
- COleChangeSourceDialog [MFC], GetToPrefix
- COleChangeSourceDialog [MFC], IsValidSource
- COleChangeSourceDialog [MFC], m_cs
ms.assetid: d0e08be7-21ef-45e1-97af-fe27d99e3bac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 376b61dbbbfe734ecc49263718902dd387c7fce8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33376447"
---
# <a name="colechangesourcedialog-class"></a>COleChangeSourceDialog – třída
Používá se pro dialogové okno OLE změnit zdroj.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleChangeSourceDialog : public COleDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleChangeSourceDialog::COleChangeSourceDialog](#colechangesourcedialog)|Vytvoří `COleChangeSourceDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleChangeSourceDialog::DoModal](#domodal)|Zobrazí dialogové okno OLE změnit zdroj.|  
|[COleChangeSourceDialog::GetDisplayName](#getdisplayname)|Získá úplný zdrojový zobrazovaný název.|  
|[COleChangeSourceDialog::GetFileName](#getfilename)|Získá název souboru z název zdroje.|  
|[COleChangeSourceDialog::GetFromPrefix](#getfromprefix)|Získá předponu předchozí zdroje.|  
|[COleChangeSourceDialog::GetItemName](#getitemname)|Získá název položky z název zdroje.|  
|[COleChangeSourceDialog::GetToPrefix](#gettoprefix)|Získá předponu nového zdroje|  
|[COleChangeSourceDialog::IsValidSource](#isvalidsource)|Označuje, jestli je platný zdroj.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COleChangeSourceDialog::m_cs](#m_cs)|Struktura, která řídí chování dialogového okna.|  
  
## <a name="remarks"></a>Poznámky  
 Vytvoření objektu třídy `COleChangeSourceDialog` když chcete volat tohoto dialogového okna. Po `COleChangeSourceDialog` objekt byl vytvořen, můžete použít [m_cs](#m_cs) struktura k chybě při inicializaci hodnoty nebo stavy, které ovládacích prvků v dialogovém okně. `m_cs` Struktura je typu [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160). Další informace o používání této třídy dialogového okna, najdete v článku [DoModal](#domodal) – členská funkce.  
  
 Další informace najdete v tématu [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktura ve Windows SDK.  
  
 Další informace o dialogových oknech OLE specifické, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleChangeSourceDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxodlgs.h  
  
##  <a name="colechangesourcedialog"></a>  COleChangeSourceDialog::COleChangeSourceDialog  
 Tato funkce vytvoří `COleChangeSourceDialog` objektu.  
  
```  
explicit COleChangeSourceDialog(
    COleClientItem* pItem,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Ukazatel na propojenou [COleClientItem](../../mfc/reference/coleclientitem-class.md) jejíž zdroj se bude aktualizovat.  
  
 `pParentWnd`  
 Odkazuje na objekt okno nadřazené nebo vlastníka (typu `CWnd`), ke které patří objektu dialogového okna. Pokud je **NULL**, nadřazeného okna dialogového okna bude nastavena pro hlavní okno aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li zobrazit dialogové okno, zavolejte [DoModal](#domodal) funkce.  
  
 Další informace najdete v tématu [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktura a [OleUIChangeSource](http://msdn.microsoft.com/library/windows/desktop/ms682497) funkce ve Windows SDK.  
  
##  <a name="domodal"></a>  COleChangeSourceDialog::DoModal  
 Volání této funkce můžete zobrazit dialogové okno OLE změnit zdroj.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Stav dokončení pro dialogové okno. Jedna z následujících hodnot:  
  
- **IDOK** Pokud úspěšně zobrazí dialogové okno.  
  
- **IDCANCEL** Pokud uživatel zrušil dialogové okno.  
  
- **IDABORT** Pokud došlo k chybě. Pokud **IDABORT** se volání vrátí, [COleDialog::GetLastError](../../mfc/reference/coledialog-class.md#getlasterror) – členská funkce získat další informace o typu Chyba, že došlo k chybě. Seznam možné chyby, najdete v článku [OleUIChangeSource](http://msdn.microsoft.com/library/windows/desktop/ms682497) funkce ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete k chybě při inicializaci různých dialogové okno Ovládací prvky nastavením členy [m_cs](#m_cs) struktura, bude třeba provést před voláním `DoModal`, ale po objektu dialogového okna je vytvořený.  
  
 Pokud `DoModal` vrátí **IDOK**, můžete volat členské funkce načíst nastavení zadaný uživatelem nebo informace z dialogového okna. Následující seznam uvádí typické dotazu funkce:  
  
- [GetFileName](#getfilename)  
  
- [Getdisplayname –](#getdisplayname)  
  
- [GetItemName](#getitemname)  
  
##  <a name="getdisplayname"></a>  COleChangeSourceDialog::GetDisplayName  
 Volání této funkce načíst se úplný zobrazovaný název pro položku propojené klienta.  
  
```  
CString GetDisplayName();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Úplný zdrojový zobrazovaný název (Přezdívka) [COleClientItem](../../mfc/reference/coleclientitem-class.md) zadaným v konstruktoru.  
  
##  <a name="getfilename"></a>  COleChangeSourceDialog::GetFileName  
 Volání této funkce můžete načíst část souboru Přezdívka zobrazovaný název pro položku propojené klienta.  
  
```  
CString GetFileName();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Část zobrazovaný název zdrojového souboru Přezdívka [COleClientItem](../../mfc/reference/coleclientitem-class.md) zadaným v konstruktoru.  
  
### <a name="remarks"></a>Poznámky  
 Soubor Přezdívka společně s Přezdívka položky poskytuje úplný zobrazovaný název.  
  
##  <a name="getfromprefix"></a>  COleChangeSourceDialog::GetFromPrefix  
 Volání této funkce můžete získat předchozí předpona řetězec pro zdroj.  
  
```  
CString GetFromPrefix();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí řetězec předpony zdroje.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce až po volání [DoModal](#domodal) vrátí **IDOK**.  
  
 Tato hodnota pochází přímo z **lpszFrom** členem [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury.  
  
 Další informace najdete v tématu [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktura ve Windows SDK.  
  
##  <a name="getitemname"></a>  COleChangeSourceDialog::GetItemName  
 Volání této funkce můžete načíst část položek Přezdívka zobrazovaný název pro položku propojené klienta.  
  
```  
CString GetItemName();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Část Přezdívka položky zobrazovaný název zdroje [COleClientItem](../../mfc/reference/coleclientitem-class.md) zadaným v konstruktoru.  
  
### <a name="remarks"></a>Poznámky  
 Soubor Přezdívka společně s Přezdívka položky poskytuje úplný zobrazovaný název.  
  
##  <a name="gettoprefix"></a>  COleChangeSourceDialog::GetToPrefix  
 Volání této funkce můžete získat nový řetězec předpony pro zdroj.  
  
```  
CString GetToPrefix();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nový řetězec předpony zdroje.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce až po volání [DoModal](#domodal) vrátí **IDOK**.  
  
 Tato hodnota pochází přímo z **lpszTo** členem [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktury.  
  
 Další informace najdete v tématu [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktura ve Windows SDK.  
  
##  <a name="m_cs"></a>  COleChangeSourceDialog::m_cs  
 Tento člen dat je struktura typu [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160).  
  
```  
OLEUICHANGESOURCE m_cs;  
```  
  
### <a name="remarks"></a>Poznámky  
 `OLEUICHANGESOURCE` slouží k řízení chování dialogových oken OLE změnit zdroj. Členové této struktury můžete přímo upravovat.  
  
 Další informace najdete v tématu [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktura ve Windows SDK.  
  
##  <a name="isvalidsource"></a>  COleChangeSourceDialog::IsValidSource  
 Volání této funkce lze zjistit nový zdroj je neplatný.  
  
```  
BOOL IsValidSource();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je nový zdroj platná, jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce až po volání [DoModal](#domodal) vrátí **IDOK**.  
  
 Další informace najdete v tématu [OLEUICHANGESOURCE](http://msdn.microsoft.com/library/windows/desktop/ms682160) struktura ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)
