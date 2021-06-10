# Playwright-based tests in GitHub workflows

End-to-end tests have never been easier than with the new [@playwright/test](https://github.com/microsoft/playwright-test): Playwright's official test runner.  
And with the help of this template, you can easily run these E2E tests in your GitHub workflows!

## Add to an existing project

1. Set up your Workflow file:
    - If you don't have a GitHub action workflow yet, copy this template's `.github/workflows/` in your project. 
    - If you already have a workflow, make sure it has the following steps:
      ```yaml
      - name: Setup Node.js
        uses: actions/setup-node@v1
        with:
          node-version: 15.x # Change this for the version of your choice
      - name: Install JS dependencies
        run: npm ci # or "npm install"
      - name: Install Playwright dependencies
        run: npx playwright install-deps
      - name: Install Playwright browsers
        run: npx playwright install
      - name: Run E2E tests
        run: npx playwright test
      ```
2. Install Playwright's test runner:
   ```bash
   npm i -D @playwright/test
   ```
3. Create your tests in the `test/` directory.  
   Ex.: 
   ```bash
   # test/test.spec.ts
   import { test, expect } from '@playwright/test';

   test('basic test', async ({ page }) => {
     await page.goto('https://playwright.dev/');
     const name = await page.innerText('.navbar__title');
     expect(name).toBe('Playwright');
   });
   ```
4. Push to GitHub, and watch your tests run in the Actions tab! 🙌   



Check out the [official @playwright/test documentation](https://playwright.dev/docs/test-intro) to learn more about how it works.
