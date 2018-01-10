---
title: "Třída COleChangeIconDialog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
dev_langs: C++
helpviewer_keywords:
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 14e6f43ce49c5e5b51a6f69a3a8952608f5bfe49
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="colechangeicondialog-class"></a>COleChangeIconDialog – třída
Používá se pro dialogové okno OLE změnit ikonu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleChangeIconDialog : public COleDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleChangeIconDialog::COleChangeIconDialog](#colechangeicondialog)|Vytvoří `COleChangeIconDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleChangeIconDialog::DoChangeIcon](#dochangeicon)|Provede změnu zadané v dialogovém okně.|  
|[COleChangeIconDialog::DoModal](#domodal)|Zobrazí dialogové okno OLE 2 změnit ikonu.|  
|[COleChangeIconDialog::GetIconicMetafile](#geticonicmetafile)|Získá popisovač pro metafile přidružené ikony formu této položky.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COleChangeIconDialog::m_ci](#m_ci)|Struktura, která řídí chování dialogového okna.|  
  
## <a name="remarks"></a>Poznámky  
 Vytvoření objektu třídy `COleChangeIconDialog` když chcete volat tohoto dialogového okna. Po `COleChangeIconDialog` objekt byl vytvořen, můžete použít [m_ci](#m_ci) struktura k chybě při inicializaci hodnoty nebo stavy, které ovládacích prvků v dialogovém okně. `m_ci` Struktura je typu **OLEUICHANGEICON**. Další informace o používání této třídy dialogového okna, najdete v článku [DoModal](#domodal) – členská funkce.  
  
 Další informace najdete v tématu [OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) struktura ve Windows SDK.  
  
 Další informace o dialogových oknech OLE specifické, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 [COleDialog](../../mfc/reference/coledialog-class.md)  
  
 `COleChangeIconDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxodlgs.h  
  
##  <a name="colechangeicondialog"></a>COleChangeIconDialog::COleChangeIconDialog  
 Tato funkce se vytvoří pouze `COleChangeIconDialog` objektu.  
  
```  
explicit COleChangeIconDialog(
    COleClientItem* pItem,  
    DWORD dwFlags = CIF_SELECTCURRENT,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Odkazuje na položku, která má být převeden.  
  
 `dwFlags`  
 Vytvoření příznak, který obsahuje libovolný počet následující hodnoty spojovat pomocí bitové hodnotě – operátor or:  
  
- **CIF_SELECTCURRENT** Určuje, že aktuální přepínač vybere původně při volání dialogové okno. Toto nastavení je výchozí.  
  
- **CIF_SELECTDEFAULT** Určuje, že výchozí přepínač vybere původně při volání dialogové okno.  
  
- **CIF_SELECTFROMFILE** Určuje, že přepínač ze souboru vybere původně při volání dialogové okno.  
  
- **CIF_SHOWHELP** Určuje, že na tlačítko Nápověda se zobrazí, když je volána dialogové okno.  
  
- **CIF_USEICONEXE** Určuje, že na ikonu by měla být rozbalena z spustitelný soubor určený v **szIconExe** pole z [m_ci](#m_ci) místo načíst z typu. To je užitečné pro vložení nebo jiných než OLE souborů.  
  
 `pParentWnd`  
 Odkazuje na objekt okno nadřazené nebo vlastníka (typu `CWnd`), ke které patří objektu dialogového okna. Pokud je **NULL**, nadřazeného okna dialogového okna bude nastavena pro hlavní okno aplikace.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li zobrazit dialogové okno, zavolejte [DoModal](#domodal) funkce.  
  
 Další informace najdete v tématu [OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) struktura ve Windows SDK.  
  
##  <a name="dochangeicon"></a>COleChangeIconDialog::DoChangeIcon  
 Volání této funkce můžete změnit ikonu představující položku do vybraného v dialogovém okně po [DoModal](#domodal) vrátí **IDOK**.  
  
```  
BOOL DoChangeIcon(COleClientItem* pItem);
```  
  
### <a name="parameters"></a>Parametry  
 `pItem`  
 Odkazuje na položku, jehož ikona se mění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je změna úspěšná; jinak 0.  
  
##  <a name="domodal"></a>COleChangeIconDialog::DoModal  
 Volání této funkce můžete zobrazit dialogové okno OLE změnit ikonu.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Stav dokončení pro dialogové okno. Jedna z následujících hodnot:  
  
- **IDOK** Pokud úspěšně zobrazí dialogové okno.  
  
- **IDCANCEL** Pokud uživatel zrušil dialogové okno.  
  
- **IDABORT** Pokud došlo k chybě. Pokud **IDABORT** se volání vrátí, `COleDialog::GetLastError` – členská funkce získat další informace o typu Chyba, že došlo k chybě. Seznam možné chyby, najdete v článku [OleUIChangeIcon](http://msdn.microsoft.com/library/windows/desktop/ms688307) funkce ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete k chybě při inicializaci různých dialogové okno Ovládací prvky nastavením členy [m_ci](#m_ci) struktura, bude třeba provést před voláním `DoModal`, ale po objektu dialogového okna je vytvořený.  
  
 Pokud `DoModal` vrátí **IDOK**, můžete volat jiné členské funkce načíst nastavení nebo informace, které se vstup uživatelem na dialogové okno.  
  
##  <a name="geticonicmetafile"></a>COleChangeIconDialog::GetIconicMetafile  
 Volání této funkce se získat popisovač pro metafile, který obsahuje ikony aspekt vybrané položky.  
  
```  
HGLOBAL GetIconicMetafile() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač metafile obsahující ikony aspekt na novou ikonu, pokud dialogové okno se zavře výběrem **OK**, jinak hodnota ikonu, protože byla předtím, než se zobrazí dialogové okno.  
  
##  <a name="m_ci"></a>COleChangeIconDialog::m_ci  
 Struktura typu **OLEUICHANGEICON** používat k ovládání chování dialogové okno Změnit ikonu.  
  
```  
OLEUICHANGEICON m_ci;  
```  
  
### <a name="remarks"></a>Poznámky  
 Členy této struktury lze změnit buď přímo nebo prostřednictvím členských funkcí.  
  
 Další informace najdete v tématu [OLEUICHANGEICON](http://msdn.microsoft.com/library/windows/desktop/ms680098) struktura ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleDialog – třída](../../mfc/reference/coledialog-class.md)
