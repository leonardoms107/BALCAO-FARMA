# Balcão Farmacêutico — Android e iOS

Aplicativo de consulta para drogarias: 285 princípios ativos com posologia, contraindicações, orientação de balcão, tipo de receita e validade, checagem de interações e comparação de marcas e preços pela tabela oficial da CMED. Funciona sem internet depois de instalado; a tabela CMED importada fica salva no aparelho.

O projeto usa o Capacitor 8: o mesmo app (pasta `www/`) roda dentro dos projetos nativos `android/` e `ios/`.

## Usar como app pelo navegador (mais simples)

Abra no Chrome do celular https://leonardoms107.github.io/BALCAO-FARMA/ e toque em ⋮ › Adicionar à tela inicial (no iPhone: Safari › Compartilhar › Adicionar à Tela de Início). Funciona sem internet depois do primeiro acesso.

## Baixar o APK pronto

No celular Android, abra:
https://github.com/leonardoms107/BALCAO-FARMA/releases/latest/download/balcao-farmaceutico.apk

## Caminho mais fácil para o Android (sem instalar nada no computador)

1. Crie uma conta gratuita no GitHub e um repositório novo (pode ser privado).
2. Envie todo o conteúdo desta pasta para o repositório (botão "Add file › Upload files" serve).
3. Abra a aba **Actions**. O fluxo **Android (APK)** roda sozinho a cada envio (ou clique em "Run workflow").
4. Em cerca de 5 a 10 minutos, baixe o arquivo `balcao-farmaceutico-apk` na página da execução.
5. No celular Android, abra o `app-debug.apk` e permita "instalar apps desta fonte".

Esse APK é de teste (assinatura de depuração). Para publicar na Google Play, gere um AAB assinado (veja abaixo).

## No computador, com Android Studio

Requisitos: Node.js 22 ou mais recente, Android Studio (com JDK 21).

```bash
npm install
npx cap sync android
npx cap open android      # abre no Android Studio
```

No Android Studio: **Build › Generate Signed App Bundle / APK** para gerar o AAB da Play Store (conta de desenvolvedor Google: taxa única de US$ 25).

## iOS (iPhone e iPad)

A Apple exige um Mac com Xcode para compilar e uma conta Apple Developer (US$ 99/ano) para instalar em aparelhos e publicar.

```bash
npm install
npx cap sync ios
npx cap open ios          # abre no Xcode
```

No Xcode: escolha seu time em **Signing & Capabilities**, conecte o iPhone e clique em Run. Para a App Store: **Product › Archive** e envie pelo TestFlight.

Sem Mac: serviços de compilação na nuvem (Codemagic, Ionic Appflow, EAS) fazem o build e o envio ao TestFlight com a sua conta Apple Developer. O fluxo `ios.yml` deste repositório só confirma que o projeto compila (macOS do GitHub, sem assinatura).

## Alternativa imediata: instalar como app web (PWA)

A pasta `www/` também funciona como PWA. Hospede-a em qualquer endereço com HTTPS (GitHub Pages, Netlify, Vercel) e, no celular, use "Adicionar à tela inicial" (Chrome no Android, Safari no iPhone). Funciona offline.

## Atualizar o conteúdo

Edite `www/index.html` (ou gere de novo a partir da fonte) e rode `npx cap sync`. Para mudar a versão do app: `android/app/build.gradle` (`versionCode`, `versionName`) e, no Xcode, *Version* e *Build*.

## Identificação do app

- Nome: Balcão Farmacêutico
- ID do pacote: `br.com.balcaofarmaceutico.app` (troque em `capacitor.config.json` antes de publicar, se quiser outro; depois rode `npx cap sync`)

## Aviso

Conteúdo de apoio à dispensação, resumido de bulas e normas sanitárias. Confirme doses e condutas na bula vigente e na prescrição. Normas consideradas: Portaria SVS/MS 344/1998 e atualizações (inclusive RDC 999/2025), RDC 471/2021, RDC 973/2025, IN 360/2025, RDC 873/2024 (SNCR) e Lei 13.732/2018.
