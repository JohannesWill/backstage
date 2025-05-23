## API Report File for "@backstage/cli-node"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts
import { JsonValue } from '@backstage/types';
import { Package } from '@manypkg/get-packages';

// @public
export type BackstagePackage = {
  dir: string;
  packageJson: BackstagePackageJson;
};

// @public (undocumented)
export type BackstagePackageFeatureType = (typeof packageFeatureType)[number];

// @public
export interface BackstagePackageJson {
  // (undocumented)
  backstage?: {
    role?: PackageRole;
    moved?: string;
    inline?: boolean;
    pluginId?: string | null;
    pluginPackage?: string;
    pluginPackages?: string[];
    features?: Record<string, BackstagePackageFeatureType>;
  };
  // (undocumented)
  bundled?: boolean;
  // (undocumented)
  dependencies?: {
    [key: string]: string;
  };
  // (undocumented)
  devDependencies?: {
    [key: string]: string;
  };
  // (undocumented)
  exports?: JsonValue;
  // (undocumented)
  files?: string[];
  // (undocumented)
  main?: string;
  // (undocumented)
  module?: string;
  // (undocumented)
  name: string;
  // (undocumented)
  optionalDependencies?: {
    [key: string]: string;
  };
  // (undocumented)
  peerDependencies?: {
    [key: string]: string;
  };
  // (undocumented)
  private?: boolean;
  // (undocumented)
  publishConfig?: {
    access?: 'public' | 'restricted';
    directory?: string;
    registry?: string;
  };
  // (undocumented)
  repository?:
    | string
    | {
        type: string;
        url: string;
        directory: string;
      };
  // (undocumented)
  scripts?: {
    [key: string]: string;
  };
  // (undocumented)
  type?: 'module' | 'commonjs';
  // (undocumented)
  types?: string;
  // (undocumented)
  typesVersions?: Record<string, Record<string, string[]>>;
  // (undocumented)
  version: string;
}

// @public
export class GitUtils {
  static listChangedFiles(ref: string): Promise<string[]>;
  static readFileAtRef(path: string, ref: string): Promise<string>;
}

// @public
export function isMonoRepo(): Promise<boolean>;

// @public
export class Lockfile {
  createSimplifiedDependencyGraph(): Map<string, Set<string>>;
  diff(otherLockfile: Lockfile): LockfileDiff;
  getDependencyTreeHash(startName: string): string;
  static load(path: string): Promise<Lockfile>;
  static parse(content: string): Lockfile;
}

// @public
export type LockfileDiff = {
  added: LockfileDiffEntry[];
  changed: LockfileDiffEntry[];
  removed: LockfileDiffEntry[];
};

// @public
export type LockfileDiffEntry = {
  name: string;
  range: string;
};

// @public
export const packageFeatureType: readonly [
  '@backstage/BackendFeature',
  '@backstage/BackstagePlugin',
  '@backstage/FrontendPlugin',
  '@backstage/FrontendModule',
];

// @public
export class PackageGraph extends Map<string, PackageGraphNode> {
  collectPackageNames(
    startingPackageNames: string[],
    collectFn: (pkg: PackageGraphNode) => Iterable<string> | undefined,
  ): Set<string>;
  static fromPackages(packages: Package[]): PackageGraph;
  listChangedPackages(options: {
    ref: string;
    analyzeLockfile?: boolean;
  }): Promise<PackageGraphNode[]>;
  static listTargetPackages(): Promise<BackstagePackage[]>;
}

// @public
export type PackageGraphNode = {
  name: string;
  dir: string;
  packageJson: BackstagePackageJson;
  allLocalDependencies: Map<string, PackageGraphNode>;
  publishedLocalDependencies: Map<string, PackageGraphNode>;
  localDependencies: Map<string, PackageGraphNode>;
  localDevDependencies: Map<string, PackageGraphNode>;
  localOptionalDependencies: Map<string, PackageGraphNode>;
  allLocalDependents: Map<string, PackageGraphNode>;
  publishedLocalDependents: Map<string, PackageGraphNode>;
  localDependents: Map<string, PackageGraphNode>;
  localDevDependents: Map<string, PackageGraphNode>;
  localOptionalDependents: Map<string, PackageGraphNode>;
};

// @public
export type PackageOutputType = 'bundle' | 'types' | 'esm' | 'cjs';

// @public
export type PackagePlatform = 'node' | 'web' | 'common';

// @public
export type PackageRole =
  | 'frontend'
  | 'backend'
  | 'cli'
  | 'web-library'
  | 'node-library'
  | 'common-library'
  | 'frontend-plugin'
  | 'frontend-plugin-module'
  | 'backend-plugin'
  | 'backend-plugin-module';

// @public
export interface PackageRoleInfo {
  // (undocumented)
  output: PackageOutputType[];
  // (undocumented)
  platform: PackagePlatform;
  // (undocumented)
  role: PackageRole;
}

// @public
export class PackageRoles {
  static detectRoleFromPackage(pkgJson: unknown): PackageRole | undefined;
  static getRoleFromPackage(pkgJson: unknown): PackageRole | undefined;
  static getRoleInfo(role: string): PackageRoleInfo;
}
```
