---
title: Nepodporované funkce CRT v aplikacích pro Univerzální platformu Windows
ms.date: 12/30/2016
ms.assetid: cbfc957d-6c60-48f4-97e3-1ed8526743b4
ms.openlocfilehash: cf67cb9c0a2438ee6ac1bcc7753c0f89b63a356d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214315"
---
# <a name="crt-functions-not-supported-in-universal-windows-platform-apps"></a>Nepodporované funkce CRT v aplikacích pro Univerzální platformu Windows

Při sestavování aplikací Univerzální platforma Windows (UWP) nejsou k dispozici mnohé funkce jazyka C runtime (CRT). V některých případech jsou k dispozici alternativní řešení – například můžete použít rozhraní API prostředí Windows Runtime nebo Win32. V ostatních případech jsou však funkce CRT zakázané, protože funkce, které je odpovídajícím nebo podpůrným rozhraním API, se nevztahují na aplikace UWP. Alternativní metodu, která je pro prostředí Windows Runtime podporovaná, najdete [v tématu alternativy k rozhraním API Windows v aplikacích pro UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Následující tabulka uvádí funkce CRT, které nejsou k dispozici při sestavování aplikací pro UWP, a označuje případná alternativní řešení.

## <a name="unsupported-crt-functions"></a>Nepodporované funkce CRT

||||
|-|-|-|
|_beep _sleep _seterrormode|Tyto funkce byly zastaralé v předchozích verzích CRT. Pro aplikace pro UWP nejsou k dispozici také odpovídající rozhraní API systému Win32.|Alternativní řešení neexistuje.|
|chdir _chdrive getcwd|Tyto funkce jsou zastaralé nebo nejsou bezpečné pro přístup z více vláken.|Použijte _chdir, _getcwd a související funkce.|
|_cgets _cgets_s _cgetws _cgetws_s _cprintf _cprintf_l _cprintf_p _cprintf_p_l _cprintf_s _cprintf_s_l _cputs _cputws _cscanf _cscanf_l _cscanf_s _cscanf_s_l _cwait _cwprintf _cwprintf_l _cwprintf_p _cwprintf_p_l _cwprintf_s _cwprintf_s_l _cwscanf _cwscanf_l _cwscanf_s _cwscanf_s_l _vcprintf _vcprintf_l _vcprintf_p _vcprintf_p_l _vcprintf_s _vcprintf_s_l _vcwprintf _vcwprintf_l _vcwprintf_p _vcwprintf_p_l _vcwprintf_s _vcwprintf_s_l _getch _getch_nolock _getche _getche_nolock _getwch _getwch_nolock _getwche _getwche_nolock _putch _putch_nolock _putwch _putwch_nolock _ungetch _ungetch_nolock _ungetwch _ungetwch_nolock _kbhit kbhit putch cgets cprintf cputs cscanf cwait getch getche ungetch|Tyto funkce se používají ke čtení a zápisu přímo z a do konzoly. Aplikace pro UWP jsou jenom grafické rozhraní (GUI). nepodporují konzolu.|Alternativní řešení neexistuje.|
|getpid|Tato funkce je zastaralá.|Použijte _getpid nebo Win32 API `GetCurrentProcessId()`.|
|_getdiskfree|Není k dispozici.|Použijte `GetDiskFreeSpaceExW()`Win32 API.|
|_getdrive _getdrives|Pro aplikace pro UWP není k dispozici odpovídající rozhraní API.|Alternativní řešení neexistuje.|
|_inp _inpd _inpw _outp _outpd _outpw INP inpd inpw outp outpd outpw|V aplikacích pro UWP se nepodporuje vstupně-výstupní operace portu.|Alternativní řešení neexistuje.|
|_ismbcalnum _ismbcalnum_l _ismbcalpha _ismbcalpha_l _ismbcdigit _ismbcdigit_l _ismbcgraph _ismbcgraph_l _ismbchira _ismbchira_l _ismbckata _ismbckata_l _ismbcl0 _ismbcl0_l _ismbcl1 _ismbcl1_l _ismbcl2 _ismbcl2_l _ismbclegal _ismbclegal_l _ismbclower _ismbclower_l _ismbcprint _ismbcprint_l _ismbcpunct _ismbcpunct_l _ismbcspace _ismbcspace_l _ismbcsymbol _ismbcsymbol_l _ismbcupper _ismbcupper_l _mbbtombc _mbbtombc_l _mbbtype _mbbtype_l _mbccpy _mbccpy_l _mbccpy_s _mbccpy_s_l _mbcjistojms _mbcjistojms_l _mbcjmstojis _mbcjmstojis_l _mbclen _mbclen_l _mbctohira _mbctohira_l _mbctokata _mbctokata_l _mbctolower _mbctolower_l _mbctombb _mbctombb_l _mbctoupper _mbctoupper_l _mbsbtype _mbsbtype_l _mbscat _mbscat_l _mbscat_s _mbscat_s_l _mbschr _mbschr_l _mbscmp _mbscmp_l _mbscoll _mbscoll_l _mbscpy _mbscpy_l _mbscpy_s _mbscpy_s_l _mbscspn _mbscspn_l _mbsdec _mbsdec_l _mbsicmp _mbsicmp_l _mbsicoll _mbsicoll_l _mbsinc _mbsinc_l _mbslen _mbslen_l _mbslwr _mbslwr_l _mbslwr_s _mbslwr_s_l _mbsnbcat _mbsnbcat_l _mbsnbcat_s _mbsnbcat_s_l _mbsnbcmp _mbsnbcmp_l _mbsnbcnt _mbsnbcnt_l _mbsnbcoll _mbsnbcoll_l _mbsnbcpy _mbsnbcpy_l _mbsnbcpy_s _mbsnbcpy_s_l _mbsnbicmp _mbsnbicmp_l _mbsnbicoll _mbsnbicoll_l _mbsnbset _mbsnbset_l _mbsnbset_s _mbsnbset_s_l _mbsncat _mbsncat_l _mbsncat_s _mbsncat_s_l _mbsnccnt _mbsnccnt_l _mbsncmp _mbsncmp_l _mbsncoll _mbsncoll_l _mbsncpy _mbsncpy_l _mbsncpy_s _mbsncpy_s_l _mbsnextc _mbsnextc_l _mbsnicmp _mbsnicmp_l _mbsnicoll _mbsnicoll_l _mbsninc _mbsninc_l _mbsnlen _mbsnlen_l _mbsnset _mbsnset_l _mbsnset_s _mbsnset_s_l _mbspbrk _mbspbrk_l _mbsrchr _mbsrchr_l _mbsrev _mbsrev_l _mbsset _mbsset_l _mbsset_s _mbsset_s_l _mbsspn _mbsspn_l _mbsspnp _mbsspnp_l _mbsstr _mbsstr_l _mbstok _mbstok_l _mbstok_s _mbstok_s_l _mbsupr _mbsupr_l _mbsupr_s _mbsupr_s_l is_wctype|Vícebajtové řetězce se v aplikacích pro UWP nepodporují.|Místo toho použijte řetězce Unicode.|
|_pclose _pipe _popen _wpopen|Funkce kanálu není pro aplikace UWP k dispozici.|Alternativní řešení neexistuje.|
|_resetstkoflw|Podpora rozhraní Win32 API není pro aplikace pro UWP dostupná.|Alternativní řešení neexistuje.|
|_getsystime _setsystime|Toto byly zastaralé rozhraní API v předchozích verzích CRT. Uživatel navíc nemůže nastavit systémový čas v aplikaci UWP z důvodu nedostatku oprávnění.|Chcete-li získat pouze systémový čas, použijte Win32 API `GetSystemTime`. Nelze nastavit systémový čas.|
|_environ _putenv _putenv_s _searchenv _searchenv_s _dupenv_s _wputenv _wputenv_s _wsearchenv getenv getenv_s putenv _wdupenv_s _wenviron _wgetenv _wgetenv_s _wsearchenv_s tzset|Proměnné prostředí nejsou k dispozici pro aplikace pro UWP.|Alternativní řešení neexistuje. Chcete-li nastavit časové pásmo, použijte _tzset.|
|_loaddll _getdllprocaddr _unloaddll|Tyto funkce byly v předchozích verzích CRT zastaralé. Uživatel také nemůže načíst knihovny DLL kromě těch, které jsou ve stejném balíčku aplikace.|Pomocí rozhraní Win32 API `LoadPackagedLibrary`, `GetProcAddress`a `FreeLibrary` načíst a použít zabalené knihovny DLL.|
|_wexecl _wexecle _wexeclp _wexeclpe _wexecv _wexecve _wexecvp _wexecvpe _execl _execle _execlp _execlpe _execv _execve _execvp _execvpe _spawnl _spawnle _spawnlp _spawnlpe _spawnv _spawnve _spawnvp _spawnvpe _wspawnl _wspawnle _wspawnlp _wspawnlpe _ wspawnv _wspawnve _wspawnvp _wspawnvpe _wsystem exec execle execlp execlpe execv execve execvp execvpe "spawnle SPAWNLP spawnlpe spawnv spawnve spawnvp spawnvpe System|Funkce není k dispozici v aplikacích pro UWP. Aplikace UWP nemůže vyvolat jinou aplikaci UWP nebo desktopovou aplikaci.|Alternativní řešení neexistuje.|
|_heapwalk _heapadd _heapchk _heapset _heapused|Tyto funkce jsou obvykle používány pro práci s haldou. V aplikacích pro UWP ale nejsou podporovaná odpovídající rozhraní API systému Win32. A aplikace už nemůžou vytvářet ani používat privátní haldy.|Alternativní řešení neexistuje. Nicméně `_heapwalk` k dispozici v modulu CRT pro ladění, pouze pro účely ladění. Tyto aplikace se nedají použít v aplikacích, které se nahrají do Microsoft Store.|

V CRT pro aplikace pro UWP jsou k dispozici následující funkce, ale měly by být použity pouze v případě, že nelze použít odpovídající rozhraní Win32 nebo prostředí Windows Runtime rozhraní API, například při přenosu velkého základu kódu.

|||
|-|-|
|Jednobajtové řetězcové funkce – například `strcat`, `strcpy`, `strlwr`a tak dále.|Zpřístupněte aplikace pro UWP výhradně v kódování Unicode, protože všechna rozhraní Win32 API a rozhraní prostředí Windows Runtime API, které jsou vystavené, používají jenom znakové sady Unicode.  Jednobajtové funkce byly ponechány pro přenos rozsáhlých základů kódu, ale měly by být využívány jinak, a pokud je to možné, měly by se místo toho používat odpovídající funkce širokého znaku.|
|Streamování vstupně-výstupních operací a souborů na nízké úrovni – například `fopen`, `open`a tak dále.|Tyto funkce jsou synchronní, což pro aplikace pro UWP nedoporučujeme. V aplikacích pro UWP použijte asynchronní rozhraní API k otevření, čtení a zápisu do souborů, abyste zabránili zamykání vlákna uživatelského rozhraní. Příklady takových rozhraní API jsou ty ve třídě `Windows::Storage::FileIO`.|

## <a name="windows-8x-store-apps-and-windows-phone-8x-apps"></a>Aplikace pro Store ve Windows 8. x a Windows Phone 8. x

Kromě výše zmíněných rozhraní API nejsou v aplikacích Windows 8. x Store a Windows Phone 8. x dostupná následující rozhraní API.

||||
|-|-|-|
|_beginthread _beginthreadex _endthread _endthreadex|Rozhraní API pro prostředí Win32 nejsou k dispozici v aplikacích pro Windows 8. x Store.|Místo toho použijte `Windows Runtime Windows::System::Threading::ThreadPool` nebo `concurrency::task`.|
|_chdir _wchdir _getcwd _getdcwd _wgetcwd _wgetdcwd|Koncept pracovního adresáře se nevztahuje na aplikace Windows 8. x Store.|Místo toho použijte úplné cesty.|
|_getpid|Tato funkce byla zastaralá v předchozích verzích CRT.|Použití Win32 API `GetCurrentProcessId()`|
|_isleadbyte_l _ismbbalnum, _ismbbalnum_l, _ismbbalpha, _ismbbalpha _ismbbalpha_l _ismbbgraph _ismbbgraph_l _ismbbkalnum _ismbbkalnum_l _ismbbkana _ismbbkana_l _ismbbkprint _ismbbkprint_l _ismbbkpunct _ismbbkpunct_l _ismbblead _ismbblead_l _ismbbprint _ismbbprint_l _ismbbpunct _ismbbpunct_l _ismbbtrail _ismbbtrail_l _ismbslead _ismbslead_l _ismbstrail _ismbstrail_l _mbsdup isleadbyte|Vícebajtové řetězce nejsou podporovány v aplikacích pro Windows 8. x Store.|Místo toho použijte řetězce Unicode.|
|_tzset|Proměnné prostředí nejsou k dispozici pro aplikace Windows 8. x Store.|Alternativní řešení neexistuje.|
|_get_heap_handle _heapmin|Odpovídající rozhraní API systému Win32 nejsou podporována v aplikacích pro Windows 8. x Store. A aplikace už nemůžou vytvářet privátní haldy.|Alternativní řešení neexistuje. `_get_heap_handle` je však k dispozici v modulu CRT pro ladění, pouze pro účely ladění.|
