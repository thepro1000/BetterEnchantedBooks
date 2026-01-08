# GitHub Actions Workflows

This directory contains automated workflows for building and publishing the Better Enchanted Books mod.

## Available Workflows

### 🔨 Build for Fabric 1.21.10

**File:** `build-fabric-1.21.10.yml`

This workflow builds the mod specifically for Minecraft Fabric 1.21.10.

**Important:** This workflow targets version **1.21.10**, not 1.21.1. These are different Minecraft versions.

#### How to Use

##### Manual Trigger

1. Go to the [Actions tab](../../actions) in GitHub
2. Select "Build for Fabric 1.21.10" from the workflows list
3. Click "Run workflow"
4. Select the branch you want to build from
5. Click "Run workflow" to start the build

##### Automatic Triggers

The workflow automatically runs on:
- Pushes to branches named `mc-1.21.10` or starting with `mc-1.21.10-`
- Pull requests targeting branches named `mc-1.21.10` or starting with `mc-1.21.10-`

#### Build Configuration

The workflow uses these versions for Fabric 1.21.10:
- **Minecraft:** 1.21.10
- **Java:** 21 (required for Minecraft 1.21+)
- **Fabric Loader:** 0.16.9
- **Yarn Mappings:** 1.21.10+build.1
- **Fabric API:** 0.110.5+1.21.10
- **Mod Menu:** 12.0.0
- **Cloth Config:** 16.0.127

#### Build Artifacts

After a successful build, the compiled JAR files will be available as workflow artifacts:
- Artifact name: `better-enchanted-books-fabric-1.21.10`
- Contains all JAR files from `build/libs/`

You can download these artifacts from the workflow run page.

#### Technical Details

The workflow:
1. Checks out the repository
2. Sets up Java 21 with Gradle caching
3. Temporarily updates `gradle.properties` with 1.21.10-specific versions
4. Builds the mod using `./gradlew clean build`
5. Uploads the built JAR files as artifacts
6. Restores the original `gradle.properties` (even if the build fails)

---

### 📦 Publish

**File:** `publish.yml`

Publishes the mod to Modrinth, CurseForge, and GitHub Releases.

This is a legacy workflow that is manually triggered via workflow dispatch. It builds and publishes from a specified branch and requires appropriate secrets (MODRINTH_TOKEN, CURSEFORGE_TOKEN, GITHUB_TOKEN) to be configured in the repository settings.
