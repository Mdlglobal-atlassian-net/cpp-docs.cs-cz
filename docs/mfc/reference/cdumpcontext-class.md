---
title: Cdumpcontext – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d80ed097056c9d52f5f9d98ab8e3f80fae431d98
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336342"
---
# <a name="cdumpcontext-class"></a>Cdumpcontext – třída
Diagnostický výstup orientovaný na stream podporuje ve formě čitelné textu.  
  
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
|[CDumpContext::DumpAsHex](#dumpashex)|Výpisy stavu systému uvedené položky v šestnáctkovém formátu.|  
|[CDumpContext::Flush](#flush)|Vyprázdní data do vyrovnávací paměti kontextu s výpisem paměti.|  
|[CDumpContext::GetDepth](#getdepth)|Získá odpovídající do hloubky výpis celého čísla.|  
|[CDumpContext::HexDump](#hexdump)|Vypíše bajtů obsažených v poli v šestnáctkovém formátu.|  
|[CDumpContext::SetDepth](#setdepth)|Nastaví hloubku výpisu paměti.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CDumpContext::operator &lt;&lt;](#operator_lt_lt)|Vloží proměnných a objektů do kontextu s výpisem paměti.|  
  
## <a name="remarks"></a>Poznámky  
 `CDumpContext` nemá základní třídu.  
  
 Můžete použít [afxDump](diagnostic-services.md#afxdump), předem deklarovaná `CDumpContext` objektu pro většinu váš výpis. `afxDump` Objekt je k dispozici pouze v ladicí verzi knihovny Microsoft Foundation Class.  
  
 Některé z paměti [diagnostické služby](../../mfc/reference/diagnostic-services.md) použít `afxDump` pro jejich výstup.  
  
 V rámci prostředí Windows, výstup z předdefinovaného `afxDump` objektu, koncepčně podobné `cerr` datového proudu, se směruje do ladicího programu pomocí funkce Windows `OutputDebugString`.  
  
 `CDumpContext` Třída nemá přetížení vložení ( **<<**) operátor pro `CObject` ukazatele, které vypíše dat tohoto objektu. Pokud potřebujete formátu vlastní s výpisem paměti pro objekt odvozené, přepište [CObject::Dump](../../mfc/reference/cobject-class.md#dump). Většina tříd Microsoft Foundation implementovat překryté `Dump` členskou funkci.  
  
 Třídy, které nejsou odvozeny od `CObject`, jako například `CString`, `CTime`, a `CTimeSpan`, mají své vlastní přetížené `CDumpContext` operátorů insertion jako struktury často používá jako `CFileStatus`, `CPoint`, a `CRect`.  
  
 Pokud používáte [IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic) nebo [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) – makro v implementaci třídy, pak `CObject::Dump` vytiskne název vaší `CObject`-odvozené třídy. V opačném případě bude tisk `CObject`.  
  
 `CDumpContext` Třídy je dostupná v ladění i vydání verze knihoven, ale `Dump` členská funkce je definováno pouze v ladicí verzi. Použití **#ifdef _DEBUG**  /  `#endif` příkazy párování diagnostiky kódu, včetně vaší vlastní `Dump` členské funkce.  
  
 Před vytvořením vlastní `CDumpContext` objektu, je nutné vytvořit `CFile` objektů, které slouží jako cíl s výpisem paměti.  
  
 Další informace o `CDumpContext`, naleznete v tématu [ladění aplikací MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
 **#define _DEBUG**  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CDumpContext`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
##  <a name="cdumpcontext"></a>  CDumpContext::CDumpContext  
 Vytvoří objekt třídy `CDumpContext`.  
  
```  
CDumpContext(CFile* pFile = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pFile*  
 Ukazatel `CFile` objekt, který je cílem s výpisem paměti.  
  
### <a name="remarks"></a>Poznámky  
 `afxDump` Objekt je vytvořen automaticky.  
  
 Nezapisujte do základního `CFile` kontextu s výpisem paměti je aktivní; jinak vrátí hodnotu, bude kolidovat s výpisem paměti. V rámci prostředí Windows, výstup se směruje na ladicí program prostřednictvím funkce Windows `OutputDebugString`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]  
  
##  <a name="dumpashex"></a>  CDumpContext::DumpAsHex  
 Vypíše zadaného typu naformátovaná jako šestnáctková čísla.  
  
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
 Voláním této členské funkce pro výpis položky zadaného typu jako šestnáctkové číslo. Chcete-li vypsat pole, volejte [CDumpContext::HexDump](#hexdump).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]  
  
##  <a name="flush"></a>  CDumpContext::Flush  
 Vynutí veškerá data ve vyrovnávací paměti k zápisu do souboru zbývá připojit ke kontextu s výpisem paměti.  
  
```  
void Flush();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]  
  
##  <a name="getdepth"></a>  CDumpContext::GetDepth  
 Určuje, zda je hloubkové nebo bez podstruktury s výpisem paměti v procesu.  
  
```  
int GetDepth() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hloubka výpis paměti jako sady podle `SetDepth`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [SetDepth](#setdepth).  
  
##  <a name="hexdump"></a>  CDumpContext::HexDump  
 Vypíše pole bajtů ve formátu jako šestnáctková čísla.  
  
```  
void HexDump(
    LPCTSTR lpszLine,  
    BYTE* pby,  
    int nBytes,  
    int nWidth);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszLine*  
 Řetězec k výstupu na začátku nového řádku.  
  
 *pby*  
 Ukazatel do vyrovnávací paměti, který obsahuje počet bajtů k výpisu paměti.  
  
 *nBytes*  
 Počet bajtů pro výpis.  
  
 *nWidth*  
 Maximální počet bajtů zálohované na řádek (ne šířku Vypsat řádek).  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li vypsat typu jeden, konkrétní položky jako šestnáctkové číslo, zavolejte [CDumpContext::DumpAsHex](#dumpashex).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]  
  
##  <a name="operator_lt_lt"></a>  CDumpContext::operator &lt;&lt;  
 Zadaný výstupní data odesílá do kontextu s výpisem paměti.  
  
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
 A `CDumpContext` odkaz. Používat návratovou hodnotu, můžete napsat více vložení na jednom řádku zdrojového kódu.  
  
### <a name="remarks"></a>Poznámky  
 Operátor vkládání je přetížena pro `CObject` ukazatele stejně jako u nejvíce primitivní typy. Ukazatel na znak výsledkem výpisu obsahu řetězce; ukazatel na **void** výsledkem adresy pouze hexadecimální s výpisem paměti. LONGLONG výsledkem výpisu 64bitové celé číslo se znaménkem; ULONGLONG výsledkem výpisu 64-bit znaménka.  
  
 Pokud používáte IMPLEMENT_DYNAMIC nebo IMPLEMENT_SERIAL – makro v implementaci vaší třídy, pak operátor vkládání prostřednictvím `CObject::Dump`, vytiskne se název vašeho `CObject`-odvozené třídy. V opačném případě bude tisk `CObject`. Pokud přepíšete `Dump` funkce třídy, pak může poskytnout lépe vystihuje výstup obsahu objektu namísto šestnáctkové s výpisem paměti.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]  
  
##  <a name="setdepth"></a>  CDumpContext::SetDepth  
 Nastaví hloubku pro výpis paměti.  
  
```  
void SetDepth(int nNewDepth);
```  
  
### <a name="parameters"></a>Parametry  
 *nNewDepth*  
 Nová hodnota hloubky.  
  
### <a name="remarks"></a>Poznámky  
 Pokud jsou vypsání primitivní typ nebo jednoduchý `CObject` , který neobsahuje žádné ukazatele na jiné objekty, pak stačí hodnotu 0. Hodnotu větší než 0 určuje hloubkové výpisu paměti, ve kterém jsou všechny objekty zálohované rekurzivně. Například hloubkové s výpisem paměti kolekce se vypsat všechny elementy z kolekce. Můžete použít jiné hodnoty konkrétní hloubka v odvozených třídách.  
  
> [!NOTE]
>  Cyklické odkazy nejsou zjištěny v hloubkové výpisů paměti a může vést k nekonečné smyčky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Cfile – třída](../../mfc/reference/cfile-class.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)
