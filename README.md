Để cấu hình report:
Bước 1: Tải thư viện 
+) marge, mochawesome , mochawesome-merge , rimraf (xóa report)
Bước 2: Vào file package.json thêm vào script
    "test:mocha-reporter": "cypress run --reporter mochawesome --reporter-options reportDir=results,overwrite=false,html=false,json=true",
    "merge-report": "mochawesome-merge results/*.json > mochawesome.json",
    "build-report": "marge mochawesome.json",
    "clean-reports": "rimraf results mochawesome.json",
    "test:full-report": "npm run clean-reports && npm run test:mocha-reporter && npm run merge-report && npm run build-report"
Bước 3: Vào file cypress.config.js
    screenshotOnRunFailure: true,
    screenshotsFolder: "./screenshots"

Bước 4: Thêm vào gitignore
    results/
    mochawesome-report/
    screenshots/

=> Run sử dụng câu lệnh:  npm run test:full-report
