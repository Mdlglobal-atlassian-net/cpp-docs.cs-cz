---
title: "Třída CDumpContext | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDumpContext
- AFX/CDumpContext
- AFX/CDumpContext::CDumpContext
- AFX/CDumpContext::DumpAsHex
- AFX/CDumpContext::Flush
- AFX/CDumpContext::GetDepth
- AFX/CDumpContext::HexDump
- AFX/CDumpContext::SetDepth
dev_langs:
- C++
helpviewer_keywords:
- CDumpContext [MFC], CDumpContext
- CDumpContext [MFC], DumpAsHex
- CDumpContext [MFC], Flush
- CDumpContext [MFC], GetDepth
- CDumpContext [MFC], HexDump
- CDumpContext [MFC], SetDepth
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5d54a461bece96faeb11f78a1788049abcabbae0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdumpcontext-class"></a>CDumpContext – třída
Výstup diagnostiky podporuje orientované datového proudu ve formě čitelný text.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDumpContext  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDumpContext::CDumpContext](#cdumpcontext)|Vytvoří `CDumpContext` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CDumpContext::DumpAsHex](#dumpashex)|Vypíše uvedené položky v šestnáctkovém formátu.|  
|[CDumpContext::Flush](#flush)|Počet vyprázdnění všechna data ve vyrovnávací paměti kontextu výpis.|  
|[CDumpContext::GetDepth](#getdepth)|Získá celé odpovídající hloubka výpis.|  
|[CDumpContext::HexDump](#hexdump)|Vypíše bajtů, které jsou obsaženy v poli v šestnáctkovém formátu.|  
|[CDumpContext::SetDepth](#setdepth)|Nastaví hloubku výpisu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDumpContext::operator&lt;&lt;](#operator_lt_lt)|Vloží proměnných a objektů do kontextu výpis.|  
  
## <a name="remarks"></a>Poznámky  
 `CDumpContext`nemá základní třídu.  
  
 Můžete použít [afxdump –](diagnostic-services.md#afxdump), predeclared `CDumpContext` objekt, pro většinu vaší rozpětí. `afxDump` Objekt je k dispozici pouze v ladicí verzi knihovny Microsoft Foundation Class.  
  
 Několik paměti [diagnostické služby](../../mfc/reference/diagnostic-services.md) použít `afxDump` pro jejich výstup.  
  
 V prostředí systému Windows, nebude výstup z předdefinovanou `afxDump` objekt koncepčně podobá `cerr` datového proudu, se směruje na ladicí program prostřednictvím funkce systému Windows **OutputDebugString**.  
  
 `CDumpContext` Třída má přetížené vložení (  **<<** ) operátor pro `CObject` ukazatele, které vypíše data objektu. Pokud potřebujete vlastní výpis formát pro objekt odvozené, mají přednost před [CObject::Dump](../../mfc/reference/cobject-class.md#dump). Většina tříd Microsoft Foundation implementovat překryté `Dump` – členská funkce.  
  
 Třídy, které nejsou odvozeny od `CObject`, jako například `CString`, `CTime`, a `CTimeSpan`, mají své vlastní přetížené `CDumpContext` operátorů insertion jako struktury proveďte často používá jako **CFileStatus**, `CPoint`, a `CRect`.  
  
 Pokud použijete [implement_dynamic –](../../mfc/reference/run-time-object-model-services.md#implement_dynamic) nebo [implement_serial –](../../mfc/reference/run-time-object-model-services.md#implement_serial) makro k implementaci třídy, pak `CObject::Dump` vypíše název vaší `CObject`-odvozené třídy. Jinak bude tisk `CObject`.  
  
 `CDumpContext` Třída je k dispozici v ladění i vydání verze knihovny, ale `Dump` – členská funkce je definována pouze v ladicí verzi. Použití **_DEBUG #ifdef –**  /  `#endif` příkazy, čímž závorka diagnostiky kódu, včetně vaše vlastní `Dump` členské funkce.  
  
 Před vytvořením vlastní `CDumpContext` objektu, musíte vytvořit `CFile` objekt, který slouží jako cíl výpis.  
  
 Další informace o `CDumpContext`, najdete v části [ladění aplikace MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
 **#define _DEBUG –**  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CDumpContext`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
##  <a name="cdumpcontext"></a>CDumpContext::CDumpContext  
 Vytvoří objekt třídy `CDumpContext`.  
  
```  
CDumpContext(CFile* pFile = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pFile`  
 Ukazatel `CFile` objekt, který je cílem výpis.  
  
### <a name="remarks"></a>Poznámky  
 `afxDump` Objekt je automaticky vytvořen.  
  
 Nezapisovat základní `CFile` při výpisu kontextu je aktivní; jinak hodnota, bude narušovat výpis. V prostředí systému Windows se výstup směruje na ladicí program prostřednictvím funkce systému Windows **OutputDebugString**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]  
  
##  <a name="dumpashex"></a>CDumpContext::DumpAsHex  
 Vypíše zadaný typ formátu hexadecimální číslice.  
  
```  
CDumpContext& DumpAsHex(BYTE b);  
CDumpContext& DumpAsHex(DWORD dw);  
CDumpContext& DumpAsHex(int n);  
CDumpContext& DumpAsHex(LONG l);  
CDumpContext& DumpAsHex(LONGLONG n);  
CDumpContext& DumpAsHex(UINT u);  
CDumpContext& DumpAsHex(ULONGLONG n);  
CDumpContext& DumpAsHex(WORD w);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na `CDumpContext` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce člena pro výpis položka zadaného typu jako o hexadecimální číslo. Chcete-li dump pole, volejte [CDumpContext::HexDump](#hexdump).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]  
  
##  <a name="flush"></a>CDumpContext::Flush  
 Vynutí veškerá data ve vyrovnávací paměti pro zápis do souboru připojit ke kontextu výpis.  
  
```  
void Flush();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]  
  
##  <a name="getdepth"></a>CDumpContext::GetDepth  
 Určuje, zda výpis hloubkového nebo omezeného v procesu.  
  
```  
int GetDepth() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hloubka výpisu jako sada podle `SetDepth`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [SetDepth](#setdepth).  
  
##  <a name="hexdump"></a>CDumpContext::HexDump  
 Vypíše pole bajtů formátovaný jako hexadecimální číslice.  
  
```  
void HexDump(
    LPCTSTR lpszLine,  
    BYTE* pby,  
    int nBytes,  
    int nWidth);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszLine*  
 Řetězec k vypsání na začátku nového řádku.  
  
 *pby*  
 Ukazatel na vyrovnávací paměť obsahující bajty k dump.  
  
 `nBytes`  
 Počet bajtů, které mají dump.  
  
 `nWidth`  
 Maximální počet bajtů zálohované na každý řádek (není šířku čáry výstup).  
  
### <a name="remarks"></a>Poznámky  
 Dump typu jeden, konkrétní položky jako o hexadecimální číslo, voláním [CDumpContext::DumpAsHex](#dumpashex).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]  
  
##  <a name="operator_lt_lt"></a>CDumpContext::operator&lt;&lt;  
 Výstupy zadaná data do kontextu výpis.  
  
```  
CDumpContext& operator<<(const CObject* pOb);  
CDumpContext& operator<<(const CObject& ob);  
CDumpContext& operator<<(LPCTSTR lpsz);  
CDumpContext& operator<<(const void* lp);  
CDumpContext& operator<<(BYTE by);  
CDumpContext& operator<<(WORD w);  
CDumpContext& operator<<(DWORD dw);  
CDumpContext& operator<<(int n);  
CDumpContext& operator<<(double d);  
CDumpContext& operator<<(float f);  
CDumpContext& operator<<(LONG l);  
CDumpContext& operator<<(UINT u);  
CDumpContext& operator<<(LPCWSTR lpsz);  
CDumpContext& operator<<(LPCSTR lpsz);  
CDumpContext& operator<<(LONGLONG n);  
CDumpContext& operator<<(ULONGLONG n);  
CDumpContext& operator<<(HWND h);  
CDumpContext& operator<<(HDC h);  
CDumpContext& operator<<(HMENU h);  
CDumpContext& operator<<(HACCEL h);  
CDumpContext& operator<<(HFONT h);
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CDumpContext` odkaz. Pomocí návratové hodnoty, můžete napsat více vložení na jeden řádek zdrojového kódu.  
  
### <a name="remarks"></a>Poznámky  
 Operátor vložení je přetížena pro `CObject` ukazatele stejně jako u nejvíce primitivní typy. Ukazatel na znak výsledkem výpis obsahu řetězce; ukazatel na `void` výsledkem hexadecimální výpis pouze adresy. A **LONGLONG** výsledkem výpis 64-bit znaménkem; A **ULONGLONG** výsledkem výpis celé číslo bez znaménka 64-bit.  
  
 Pokud použijete `IMPLEMENT_DYNAMIC` nebo `IMPLEMENT_SERIAL` makro k implementaci třídě, pak se operátor vložení prostřednictvím `CObject::Dump`, vytiskne název vaší `CObject`-odvozené třídy. Jinak bude tisk `CObject`. Pokud přepíšete `Dump` funkce třídu, pak může poskytnout smysluplnější výstup obsah objektu namísto šestnáctkové výpis.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]  
  
##  <a name="setdepth"></a>CDumpContext::SetDepth  
 Nastaví hloubku pro výpis.  
  
```  
void SetDepth(int nNewDepth);
```  
  
### <a name="parameters"></a>Parametry  
 *nNewDepth*  
 Nová hodnota hloubka.  
  
### <a name="remarks"></a>Poznámky  
 Pokud jsou vypsání primitivní typ nebo jednoduchý `CObject` obsahující žádné ukazatele na další objekty a pak stačí s hodnotou 0. Hodnotu větší než 0 určuje výpis hloubkové, kde jsou všechny objekty zálohované rekurzivně. Výpis hloubkové kolekce bude například dump všechny elementy z kolekce. Můžete použít jiné hodnoty konkrétní hloubka v odvozených třídách.  
  
> [!NOTE]
>  Cyklické odkazy nejsou zjištěny v hloubkové výpisy což může vést k nekonečné smyčky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Cfile – třída](../../mfc/reference/cfile-class.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)
