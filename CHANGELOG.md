# Changelog

## [4.0.0](https://github.com/RobeWuXin/treehouse/compare/v3.1.8...v4.0.0) (2026-11-24)


### ⚠ BREAKING CHANGES

* **cmd:** `treehouse return` now exits 3, not 0, when it leaves a dirty worktree in place, and `treehouse get` does the same when its subshell exits leaving one dirty. Callers that read exit 0 as "the slot was released" were reading the bug this fixes; scripts under `set -e`, or using `treehouse return "$p" && next-step`, will now stop or branch differently at a dirty abort. Pass --force to clean and return, or treat exit 3 as "not returned".
* **cmd:** the `treehouse destroy --force` flag is removed. Replace it with the specific --include-unlanded / --include-in-use / --include-leased flag(s) for the risk you intend to override, plus --yes, and pass an explicit pool path to --all.

### Features

* add --root flag and TREEHOUSE_ROOT env for the worktree root ([#93](https://github.com/RobeWuXin/treehouse/issues/93)) ([e443e55](https://github.com/RobeWuXin/treehouse/commit/e443e55435e67ebc2a65eba22076b543531d4215))
* add Nix package manager install support ([#113](https://github.com/RobeWuXin/treehouse/issues/113)) ([09ccbfc](https://github.com/RobeWuXin/treehouse/commit/09ccbfce82c64d684240fd80a4a05d1f67f1ffb8))
* add no-fetch worktree acquisition ([d8a76d7](https://github.com/RobeWuXin/treehouse/commit/d8a76d74c8112420ca3422e01cb10ad870a2c93f))
* add opt-in branch creation to treehouse get ([#150](https://github.com/RobeWuXin/treehouse/issues/150)) ([6823716](https://github.com/RobeWuXin/treehouse/commit/68237161bc99b080886c4ebf007ef28cc82c10fc))
* add per-acquisition file seeding manifests ([#131](https://github.com/RobeWuXin/treehouse/issues/131)) ([b511387](https://github.com/RobeWuXin/treehouse/commit/b5113878ceb7e1e461249cecfd0847a38f93b040))
* **cmd:** add global prune mode ([#26](https://github.com/RobeWuXin/treehouse/issues/26)) ([ca17bea](https://github.com/RobeWuXin/treehouse/commit/ca17beaa1082cc13dab29b1564e154b760757e4a))
* **cmd:** make destroy safe by default ([#37](https://github.com/RobeWuXin/treehouse/issues/37)) ([624e369](https://github.com/RobeWuXin/treehouse/commit/624e36976824d983edaa284de7310ffa5c167f9e))
* **cmd:** report checked-out branches in status ([#134](https://github.com/RobeWuXin/treehouse/issues/134)) ([10924c4](https://github.com/RobeWuXin/treehouse/commit/10924c4eb76579f6e79146c18ef38ca75f72df54))
* **cmd:** return a worktree by name and add return --all ([#143](https://github.com/RobeWuXin/treehouse/issues/143)) ([70d23fd](https://github.com/RobeWuXin/treehouse/commit/70d23fd8d616232e1a9d4187400d9741a6e9946b))
* **config:** add configurable root for pool directory ([#12](https://github.com/RobeWuXin/treehouse/issues/12)) ([5ca17d2](https://github.com/RobeWuXin/treehouse/commit/5ca17d2e03fcaa82c790a7a66e1db49d185b28e7))
* **fileclone:** add opt-in APFS sharing for fresh Git worktrees ([#153](https://github.com/RobeWuXin/treehouse/issues/153)) ([493fbcd](https://github.com/RobeWuXin/treehouse/commit/493fbcd56024bb31914cc178405b8127d4d0c3e4))
* initial project setup ([8e27a62](https://github.com/RobeWuXin/treehouse/commit/8e27a625110c8e2925652945ce88444de1a3eed3))
* **nix:** add flake.nix and flake.lock ([#15](https://github.com/RobeWuXin/treehouse/issues/15)) ([9dd8cd0](https://github.com/RobeWuXin/treehouse/commit/9dd8cd0906a88db3b2b664435c0aa036c6250c61))
* **pool:** add durable worktree leases ([#35](https://github.com/RobeWuXin/treehouse/issues/35)) ([4a0d370](https://github.com/RobeWuXin/treehouse/commit/4a0d37026678017489a7ee8391c68f9ea02fddb8))
* **pool:** add lease command to durably lease an existing worktree ([#128](https://github.com/RobeWuXin/treehouse/issues/128)) ([2bfebe2](https://github.com/RobeWuXin/treehouse/commit/2bfebe2ead456a6334139742b09305961f80ba44))
* **pool:** add return --if-clean ([#217](https://github.com/RobeWuXin/treehouse/issues/217)) ([5b5baef](https://github.com/RobeWuXin/treehouse/commit/5b5baef4627b2bd5630945157edaa856df98f9e7))
* **pool:** add stable lease identities ([#68](https://github.com/RobeWuXin/treehouse/issues/68)) ([7872d28](https://github.com/RobeWuXin/treehouse/commit/7872d2854068426cebfbb55d86ced89801df775c))
* **pool:** add user lifecycle hooks ([#22](https://github.com/RobeWuXin/treehouse/issues/22)) ([d3b3f6b](https://github.com/RobeWuXin/treehouse/commit/d3b3f6b02ceb14006495a7df604458a69f7c4016))
* **pool:** automatically free safe recovered slots ([#159](https://github.com/RobeWuXin/treehouse/issues/159)) ([fb7a26f](https://github.com/RobeWuXin/treehouse/commit/fb7a26f535fa924716af23b6f5a403bee2d862f1))
* **pool:** classify orphaned worktrees during prune ([#28](https://github.com/RobeWuXin/treehouse/issues/28)) ([b94c125](https://github.com/RobeWuXin/treehouse/commit/b94c125df8300b6c141c1997405856291fff5fad))
* **pool:** make where a new pool worktree is placed configurable ([#140](https://github.com/RobeWuXin/treehouse/issues/140)) ([d597c67](https://github.com/RobeWuXin/treehouse/commit/d597c676f4004ea39929f5737401e2e087ae089a))
* **pool:** opt-in unique worktree directory names for get ([#126](https://github.com/RobeWuXin/treehouse/issues/126)) ([017e86b](https://github.com/RobeWuXin/treehouse/commit/017e86b2f6005bb73cf4c8d69c8d57e376c97c3c))
* **pool:** seed ignored files from .worktreeinclude ([#129](https://github.com/RobeWuXin/treehouse/issues/129)) ([8d26b2d](https://github.com/RobeWuXin/treehouse/commit/8d26b2d5abba4759afc21626d0bdae8be12323e9))
* **pool:** support configurable base branch for get ([#119](https://github.com/RobeWuXin/treehouse/issues/119)) ([da3202c](https://github.com/RobeWuXin/treehouse/commit/da3202c5eaa0f7e51376a8948809fa697628e60f))
* **prune:** add safe stale worktree pruning ([#24](https://github.com/RobeWuXin/treehouse/issues/24)) ([933b468](https://github.com/RobeWuXin/treehouse/commit/933b468aea5b65011fde0db3ff9f1cb554a103a1))
* **status:** show current worktree status ([596b1dd](https://github.com/RobeWuXin/treehouse/commit/596b1ddc168acae27f4ce6e1b838948aea0d605c))
* use latest default branch for worktree ([d5df797](https://github.com/RobeWuXin/treehouse/commit/d5df797ba985071eabdcf3ee021ec3c7b13f1b99))
* **vcs:** add opt-in Jujutsu (jj) workspace backend behind a VCS seam ([#100](https://github.com/RobeWuXin/treehouse/issues/100)) ([358e450](https://github.com/RobeWuXin/treehouse/commit/358e4505e120ad7103cd7d7b7eeb66dd031f5606))
* **vcs:** slot-flavor dispatch, flavor-aware acquire, and markerless fail-closed hardening ([#110](https://github.com/RobeWuXin/treehouse/issues/110)) ([7b52809](https://github.com/RobeWuXin/treehouse/commit/7b5280909845c2d7155c9e7b0451aa02d9c7bdcc))


### Bug Fixes

* add /v3 major version suffix to module path ([#167](https://github.com/RobeWuXin/treehouse/issues/167)) ([df0cfd9](https://github.com/RobeWuXin/treehouse/commit/df0cfd99588f8d5a83523891708dac39fa4f7031))
* app update permission error ([5b45b23](https://github.com/RobeWuXin/treehouse/commit/5b45b238dfc0656ca5637c07f82ae63a5487cf9d))
* CI failures ([262fbe3](https://github.com/RobeWuXin/treehouse/commit/262fbe3bcb37b8df66cdc592aaa9f4a483384590))
* **ci:** make update-vendor-hash fork-aware for checkout and push ([#105](https://github.com/RobeWuXin/treehouse/issues/105)) ([aca0a98](https://github.com/RobeWuXin/treehouse/commit/aca0a9820843a70e64ed32998bb9d78bcc0df211))
* **ci:** suppress pull_request runs on release-please PRs ([#77](https://github.com/RobeWuXin/treehouse/issues/77)) ([4d6b5b1](https://github.com/RobeWuXin/treehouse/commit/4d6b5b1aa8559b03a9a6bd49628a32ff81a46ae4))
* **cli:** expose version flag and set rootCmd.Version ([54919c3](https://github.com/RobeWuXin/treehouse/commit/54919c394c0b7cefc008020a93a72ec12db1dbb9))
* **cmd:** detach worktrees before pool reuse ([#19](https://github.com/RobeWuXin/treehouse/issues/19)) ([fb3bae0](https://github.com/RobeWuXin/treehouse/commit/fb3bae09b5bccbf7b684ed1b09d4034d5cc4028d))
* **cmd:** exit non-zero when a dirty worktree is not returned ([#138](https://github.com/RobeWuXin/treehouse/issues/138)) ([a13d5d1](https://github.com/RobeWuXin/treehouse/commit/a13d5d1d2219c691bf22b928fd08c69445ab5d7a))
* **cmd:** paste-safe dirty non-TTY return --force hints ([#122](https://github.com/RobeWuXin/treehouse/issues/122)) ([1b47563](https://github.com/RobeWuXin/treehouse/commit/1b475639f0458b5cb46e8204596aead8b5dba130))
* **cmd:** resolve main repo root for pool commands run inside a worktree ([#51](https://github.com/RobeWuXin/treehouse/issues/51)) ([e48b27e](https://github.com/RobeWuXin/treehouse/commit/e48b27e7be5d3732f95d57ee6c1009dcc0423c4c))
* **config:** warn when repository hooks are ignored ([#141](https://github.com/RobeWuXin/treehouse/issues/141)) ([3496e2e](https://github.com/RobeWuXin/treehouse/commit/3496e2e669cd07a5903c809015e013ac86e49dee))
* detect squash-merged worktrees ([#88](https://github.com/RobeWuXin/treehouse/issues/88)) ([232700b](https://github.com/RobeWuXin/treehouse/commit/232700b41149ea69839cfe06747088fb9e86d1c3))
* **get:** skip reclaiming a pool slot that holds unlanded work ([#104](https://github.com/RobeWuXin/treehouse/issues/104)) ([c108f5f](https://github.com/RobeWuXin/treehouse/commit/c108f5fbe81c9f17069b8d657259c7e858f0f846))
* ignore in-project pool via .git/info/exclude ([da83c79](https://github.com/RobeWuXin/treehouse/commit/da83c7936991bcd46f9e5444b21161ac8a629b6e))
* install under ~/.local/bin when in PATH ([8ed1058](https://github.com/RobeWuXin/treehouse/commit/8ed1058612650a657aacf7e03a378fc6e52ff372))
* **installer:** resolve latest release without GitHub API ([#197](https://github.com/RobeWuXin/treehouse/issues/197)) ([ea5776c](https://github.com/RobeWuXin/treehouse/commit/ea5776cfdaf5b7cf15853f6c368c8b9d5620841a))
* **nix:** drop x86_64-darwin and update flake.lock ([#182](https://github.com/RobeWuXin/treehouse/issues/182)) ([6eac258](https://github.com/RobeWuXin/treehouse/commit/6eac258b400119dee1cf1a176341d19c838ce974))
* pin nix-build to flake-locked nixpkgs and extract package.nix ([#135](https://github.com/RobeWuXin/treehouse/issues/135)) ([0c9eed8](https://github.com/RobeWuXin/treehouse/commit/0c9eed8257ab22c5c153bf157b0fd7d9763ca876))
* **pool:** adopt pre-3.0 state instead of quarantining it as recovered ([#156](https://github.com/RobeWuXin/treehouse/issues/156)) ([d8478b9](https://github.com/RobeWuXin/treehouse/commit/d8478b909e193a4a7a41ad88b29291e9207001c1))
* **pool:** guard against invalid worktree registrations ([#200](https://github.com/RobeWuXin/treehouse/issues/200)) ([c751cff](https://github.com/RobeWuXin/treehouse/commit/c751cffb08411f312a3f623c63f8603fcfb19b22))
* **pool:** let prune and destroy reclaim worktrees from other clones in a shared pool ([#146](https://github.com/RobeWuXin/treehouse/issues/146)) ([fe0fd7c](https://github.com/RobeWuXin/treehouse/commit/fe0fd7cc97224d378918c5dd7e22874bd6780206))
* **pool:** make state persistence atomic and recoverable ([#55](https://github.com/RobeWuXin/treehouse/issues/55)) ([fb7651d](https://github.com/RobeWuXin/treehouse/commit/fb7651d246fe6e301d855f57bbaa66d05a64c6e4))
* **pool:** merge state entries that record one worktree under two paths ([#215](https://github.com/RobeWuXin/treehouse/issues/215)) ([55282e1](https://github.com/RobeWuXin/treehouse/commit/55282e1e3735b0602c8fbbc9fbcb5c22334409bf))
* **pool:** preserve worktree identity across symlinked pool paths ([#208](https://github.com/RobeWuXin/treehouse/issues/208)) ([aed94fb](https://github.com/RobeWuXin/treehouse/commit/aed94fb43419eb1348d91d0d3c521639c48bae49))
* **pool:** prune stale worktree registrations before adding in get ([6d60a7f](https://github.com/RobeWuXin/treehouse/commit/6d60a7fb02ef11909ca436753ac1bda7e21c4d1c)), closes [#31](https://github.com/RobeWuXin/treehouse/issues/31)
* **pool:** reclaim empty leftover slot directories on get ([#186](https://github.com/RobeWuXin/treehouse/issues/186)) ([d6133bd](https://github.com/RobeWuXin/treehouse/commit/d6133bdd673cbfba2e182ce7a65a776cf20d2903))
* **pool:** report only the processes return would terminate in status ([#139](https://github.com/RobeWuXin/treehouse/issues/139)) ([285ddb1](https://github.com/RobeWuXin/treehouse/commit/285ddb10a02d38ee6d3064a8ba5cf21185cca2c5))
* **pool:** reuse a pooled worktree only for the clone that owns it ([#145](https://github.com/RobeWuXin/treehouse/issues/145)) ([8bebb58](https://github.com/RobeWuXin/treehouse/commit/8bebb58e1f3d97abcc0e919337622a2bec7c1407))
* **pool:** stop get from deregistering live slots it cannot see ([#198](https://github.com/RobeWuXin/treehouse/issues/198)) ([2327c1b](https://github.com/RobeWuXin/treehouse/commit/2327c1b2fb3a17ca683e33bbf300970b35a7448e)), closes [#194](https://github.com/RobeWuXin/treehouse/issues/194)
* **process:** safely clean up lingering worktree processes ([#17](https://github.com/RobeWuXin/treehouse/issues/17)) ([df64579](https://github.com/RobeWuXin/treehouse/commit/df64579775e8ea7e578aa7b9f2eed5b062652e72))
* **process:** wait for SIGKILLed processes to be reaped before return runs git ([#102](https://github.com/RobeWuXin/treehouse/issues/102)) ([40d6c89](https://github.com/RobeWuXin/treehouse/commit/40d6c8965b872753f3fc530fecb58029637802f3))
* recheck app update when cached version is stale ([9a919b7](https://github.com/RobeWuXin/treehouse/commit/9a919b76398916c13b09db6c0f2c43e2e9bfdddb))
* **return:** refuse to reset a worktree that still has live writers ([#103](https://github.com/RobeWuXin/treehouse/issues/103)) ([fe6ad98](https://github.com/RobeWuXin/treehouse/commit/fe6ad981334fd3c30d5dad25936d9d542b9f4ce9))
* **shell:** start supported user shells as interactive login sessions ([#120](https://github.com/RobeWuXin/treehouse/issues/120)) ([c952a1c](https://github.com/RobeWuXin/treehouse/commit/c952a1cc527f8377b503136b426c9211331bb65f))
* shorter version display ([ff8702f](https://github.com/RobeWuXin/treehouse/commit/ff8702f180dc6fa65db8cb6662911c84e1abb4da))
* update repository URLs ([2da12cc](https://github.com/RobeWuXin/treehouse/commit/2da12ccac294980d676dff57e6835caeee6448b4))
* update vendor hash handling in workflow ([2ab127a](https://github.com/RobeWuXin/treehouse/commit/2ab127a601065b145d918efd5a1da1c6f020e21f))
* **update:** refuse self-update and silence the notice in the Nix store ([#180](https://github.com/RobeWuXin/treehouse/issues/180)) ([875bb77](https://github.com/RobeWuXin/treehouse/commit/875bb775df23db3bad63abb64e78a402f2dc3d01))
* **updater:** keep update-check cache fresh when install is up to date ([#213](https://github.com/RobeWuXin/treehouse/issues/213)) ([0291f2e](https://github.com/RobeWuXin/treehouse/commit/0291f2e2a5766fdefa41f16ab861305eddd585ff))
* **updater:** replace a running Windows exe without a fixed .old backup ([#121](https://github.com/RobeWuXin/treehouse/issues/121)) ([f4cb2b0](https://github.com/RobeWuXin/treehouse/commit/f4cb2b0e39b65018dae26c71c9708750c66192c1))
* use remote URL for pool hash for local repos ([f199982](https://github.com/RobeWuXin/treehouse/commit/f199982ff07d5e692bc6e45fdc279b87637553f0))
* **vcs:** check recovered HEAD containment with a single rev-list walk ([#164](https://github.com/RobeWuXin/treehouse/issues/164)) ([ff42861](https://github.com/RobeWuXin/treehouse/commit/ff428613316dea2deb2367f429dcb5db8a22e46b))
* **vcs:** move HEAD through a git transaction on reftable repositories ([#175](https://github.com/RobeWuXin/treehouse/issues/175)) ([d6e9804](https://github.com/RobeWuXin/treehouse/commit/d6e9804977af918e64877fe21b5e92ccad0a21d3)), closes [#174](https://github.com/RobeWuXin/treehouse/issues/174)
* **vcs:** pin submodule.recurse=false in git runners ([#177](https://github.com/RobeWuXin/treehouse/issues/177)) ([df72414](https://github.com/RobeWuXin/treehouse/commit/df72414ec0aeccf84366126720624c3aced11ae0))
* **vcs:** recover stale HEAD.lock left by interrupted worktree reset ([#178](https://github.com/RobeWuXin/treehouse/issues/178)) ([ea6d6b8](https://github.com/RobeWuXin/treehouse/commit/ea6d6b8af9341829696fe1098c2a0dc8ef956524))
* windows test failure ([7d15a73](https://github.com/RobeWuXin/treehouse/commit/7d15a7375ffd8eef923f7757088fd9c6f8f6f972))

## [3.1.8](https://github.com/kunchenguid/treehouse/compare/v3.1.7...v3.1.8) (2026-10-30)


### Bug Fixes

* **pool:** guard against invalid worktree registrations ([#200](https://github.com/kunchenguid/treehouse/issues/200)) ([bf61797](https://github.com/kunchenguid/treehouse/commit/bf61797bb80a0b1169dbb736e43111181a7ef472))
* **vcs:** recover stale HEAD.lock left by interrupted worktree reset ([#178](https://github.com/kunchenguid/treehouse/issues/178)) ([986b4b7](https://github.com/kunchenguid/treehouse/commit/986b4b735fd9c20b02dc9ab48311a79344247943))

## [3.1.7](https://github.com/kunchenguid/treehouse/compare/v3.1.6...v3.1.7) (2026-10-26)


### Bug Fixes

* **installer:** resolve latest release without GitHub API ([#197](https://github.com/kunchenguid/treehouse/issues/197)) ([7372295](https://github.com/kunchenguid/treehouse/commit/73722955948dd402e0245b65dd9e5418b7970112))
* **pool:** stop get from deregistering live slots it cannot see ([#198](https://github.com/kunchenguid/treehouse/issues/198)) ([4acb9e4](https://github.com/kunchenguid/treehouse/commit/4acb9e4bc1d78d9aeb69358cd5ff7d1b375a3a1f)), closes [#194](https://github.com/kunchenguid/treehouse/issues/194)

## [3.1.6](https://github.com/kunchenguid/treehouse/compare/v3.1.5...v3.1.6) (2026-10-24)


### Bug Fixes

* **vcs:** move HEAD through a git transaction on reftable repositories ([#175](https://github.com/kunchenguid/treehouse/issues/175)) ([f389758](https://github.com/kunchenguid/treehouse/commit/f389758894dc2480801f3151ac272e8a3b7920e1)), closes [#174](https://github.com/kunchenguid/treehouse/issues/174)

## [3.1.5](https://github.com/kunchenguid/treehouse/compare/v3.1.4...v3.1.5) (2026-10-20)


### Bug Fixes

* **pool:** reclaim empty leftover slot directories on get ([#186](https://github.com/kunchenguid/treehouse/issues/186)) ([03c12c2](https://github.com/kunchenguid/treehouse/commit/03c12c2847f2fa347e98e0a2e382fbde40a60da0))

## [3.1.4](https://github.com/kunchenguid/treehouse/compare/v3.1.3...v3.1.4) (2026-10-15)


### Bug Fixes

* **nix:** drop x86_64-darwin and update flake.lock ([#182](https://github.com/kunchenguid/treehouse/issues/182)) ([2a93409](https://github.com/kunchenguid/treehouse/commit/2a934095cc791845f4b689ce9a5379df6d20df39))
* **update:** refuse self-update and silence the notice in the Nix store ([#180](https://github.com/kunchenguid/treehouse/issues/180)) ([93a18da](https://github.com/kunchenguid/treehouse/commit/93a18dabcf5ad46bf243492912865d65ef0977dd))

## [3.1.3](https://github.com/kunchenguid/treehouse/compare/v3.1.2...v3.1.3) (2026-10-12)


### Bug Fixes

* **vcs:** pin submodule.recurse=false in git runners ([#177](https://github.com/kunchenguid/treehouse/issues/177)) ([d40678e](https://github.com/kunchenguid/treehouse/commit/d40678e3b88ac638c4c05ccdfd96082c1aa1648a))

## [3.1.2](https://github.com/kunchenguid/treehouse/compare/v3.1.1...v3.1.2) (2026-10-02)


### Bug Fixes

* add /v3 major version suffix to module path ([#167](https://github.com/kunchenguid/treehouse/issues/167)) ([2b481be](https://github.com/kunchenguid/treehouse/commit/2b481beda1bac61669b6435ac8cae2f58be5f36e))

## [3.1.1](https://github.com/kunchenguid/treehouse/compare/v3.1.0...v3.1.1) (2026-09-30)


### Bug Fixes

* **vcs:** check recovered HEAD containment with a single rev-list walk ([#164](https://github.com/kunchenguid/treehouse/issues/164)) ([cb7fb26](https://github.com/kunchenguid/treehouse/commit/cb7fb264d138da9e6f0234d7e19aa42239413268))

## [3.1.0](https://github.com/kunchenguid/treehouse/compare/v3.0.1...v3.1.0) (2026-09-26)


### Features

* **pool:** automatically free safe recovered slots ([#159](https://github.com/kunchenguid/treehouse/issues/159)) ([d1f9167](https://github.com/kunchenguid/treehouse/commit/d1f91675d956e8619d45b102c209fe3e612c007a))

## [3.0.1](https://github.com/kunchenguid/treehouse/compare/v3.0.0...v3.0.1) (2026-09-26)


### Bug Fixes

* **pool:** adopt pre-3.0 state instead of quarantining it as recovered ([#156](https://github.com/kunchenguid/treehouse/issues/156)) ([706ae59](https://github.com/kunchenguid/treehouse/commit/706ae5932b13a355db5698486042f0b897eea247))

## [3.0.0](https://github.com/kunchenguid/treehouse/compare/v2.3.0...v3.0.0) (2026-09-25)


### ⚠ BREAKING CHANGES

* **cmd:** `treehouse return` now exits 3, not 0, when it leaves a dirty worktree in place, and `treehouse get` does the same when its subshell exits leaving one dirty. Callers that read exit 0 as "the slot was released" were reading the bug this fixes; scripts under `set -e`, or using `treehouse return "$p" && next-step`, will now stop or branch differently at a dirty abort. Pass --force to clean and return, or treat exit 3 as "not returned".

### Features

* add Nix package manager install support ([#113](https://github.com/kunchenguid/treehouse/issues/113)) ([4307a30](https://github.com/kunchenguid/treehouse/commit/4307a30f6d18457200dbd15954a56d75749454b8))
* add opt-in branch creation to treehouse get ([#150](https://github.com/kunchenguid/treehouse/issues/150)) ([e4f59d1](https://github.com/kunchenguid/treehouse/commit/e4f59d10b872eb8d191ef16ccfb073b505a262e2))
* add per-acquisition file seeding manifests ([#131](https://github.com/kunchenguid/treehouse/issues/131)) ([67c9f2f](https://github.com/kunchenguid/treehouse/commit/67c9f2fd5e662321b3481255ffa633540d5d793e))
* **cmd:** report checked-out branches in status ([#134](https://github.com/kunchenguid/treehouse/issues/134)) ([ee8652b](https://github.com/kunchenguid/treehouse/commit/ee8652b8464ae1d673053a627e7dad75ac2f3406))
* **cmd:** return a worktree by name and add return --all ([#143](https://github.com/kunchenguid/treehouse/issues/143)) ([99f4db2](https://github.com/kunchenguid/treehouse/commit/99f4db2bbeececc1e6f136a88f79002e5a707174))
* **fileclone:** add opt-in APFS sharing for fresh Git worktrees ([#153](https://github.com/kunchenguid/treehouse/issues/153)) ([438e9c1](https://github.com/kunchenguid/treehouse/commit/438e9c17d29632dd2c17765225c11de1086d6aad))
* **pool:** add lease command to durably lease an existing worktree ([#128](https://github.com/kunchenguid/treehouse/issues/128)) ([b227e59](https://github.com/kunchenguid/treehouse/commit/b227e59cf73fd15d69f00b580da0f5bee6b38fce))
* **pool:** make where a new pool worktree is placed configurable ([#140](https://github.com/kunchenguid/treehouse/issues/140)) ([6d33753](https://github.com/kunchenguid/treehouse/commit/6d33753e94ac3ddf08d7953f3e200ba9bb8b00d5))
* **pool:** opt-in unique worktree directory names for get ([#126](https://github.com/kunchenguid/treehouse/issues/126)) ([cee9ea1](https://github.com/kunchenguid/treehouse/commit/cee9ea11337afea0e5e1431317b81200d4e8bd18))
* **pool:** seed ignored files from .worktreeinclude ([#129](https://github.com/kunchenguid/treehouse/issues/129)) ([0e87c62](https://github.com/kunchenguid/treehouse/commit/0e87c62b0494fd08bc5df230797cfb44a10dd814))
* **pool:** support configurable base branch for get ([#119](https://github.com/kunchenguid/treehouse/issues/119)) ([c98e9de](https://github.com/kunchenguid/treehouse/commit/c98e9de0a8ad85d9551ccce85ecd96c8b9a8dff5))


### Bug Fixes

* **cmd:** exit non-zero when a dirty worktree is not returned ([#138](https://github.com/kunchenguid/treehouse/issues/138)) ([e57daab](https://github.com/kunchenguid/treehouse/commit/e57daab3e0c038750d251c779d1c3e294156fa7f))
* **cmd:** paste-safe dirty non-TTY return --force hints ([#122](https://github.com/kunchenguid/treehouse/issues/122)) ([59762c9](https://github.com/kunchenguid/treehouse/commit/59762c9dd545cca29517e6b7333ec5a23e67ee85))
* **config:** warn when repository hooks are ignored ([#141](https://github.com/kunchenguid/treehouse/issues/141)) ([8e3ceff](https://github.com/kunchenguid/treehouse/commit/8e3ceffb090d335ea459fa5bd53754ac3a87b6b4))
* pin nix-build to flake-locked nixpkgs and extract package.nix ([#135](https://github.com/kunchenguid/treehouse/issues/135)) ([30723fc](https://github.com/kunchenguid/treehouse/commit/30723fc0baa2ce05969c96dd245a163333945596))
* **pool:** let prune and destroy reclaim worktrees from other clones in a shared pool ([#146](https://github.com/kunchenguid/treehouse/issues/146)) ([94c092f](https://github.com/kunchenguid/treehouse/commit/94c092f511259c21dffb7466feb9048e29913176))
* **pool:** report only the processes return would terminate in status ([#139](https://github.com/kunchenguid/treehouse/issues/139)) ([af57b33](https://github.com/kunchenguid/treehouse/commit/af57b33ff8a80b3b1b476b3f060677a3271201a5))
* **pool:** reuse a pooled worktree only for the clone that owns it ([#145](https://github.com/kunchenguid/treehouse/issues/145)) ([1185dc6](https://github.com/kunchenguid/treehouse/commit/1185dc6cc50e1b66ef5c74b8ac677a6251258abc))
* **shell:** start supported user shells as interactive login sessions ([#120](https://github.com/kunchenguid/treehouse/issues/120)) ([db06078](https://github.com/kunchenguid/treehouse/commit/db06078c6f5569e539b8cdb7703f38fdefe06382))
* **updater:** replace a running Windows exe without a fixed .old backup ([#121](https://github.com/kunchenguid/treehouse/issues/121)) ([bdbd0f8](https://github.com/kunchenguid/treehouse/commit/bdbd0f89164ba87cda5d48b53dfb3e04836dc6f7))

## [2.3.0](https://github.com/kunchenguid/treehouse/compare/v2.2.1...v2.3.0) (2026-08-21)


### Features

* **vcs:** add opt-in Jujutsu (jj) workspace backend behind a VCS seam ([#100](https://github.com/kunchenguid/treehouse/issues/100)) ([a2e554c](https://github.com/kunchenguid/treehouse/commit/a2e554c15e0c8de0e8cbc0e45549acc59f6b97f9))
* **vcs:** slot-flavor dispatch, flavor-aware acquire, and markerless fail-closed hardening ([#110](https://github.com/kunchenguid/treehouse/issues/110)) ([c88b53e](https://github.com/kunchenguid/treehouse/commit/c88b53ef6149054435fd375806117dfcd8371a0d))


### Bug Fixes

* **ci:** make update-vendor-hash fork-aware for checkout and push ([#105](https://github.com/kunchenguid/treehouse/issues/105)) ([6c40205](https://github.com/kunchenguid/treehouse/commit/6c40205c69855998ed2fac19d3c75751b504243a))
* **get:** skip reclaiming a pool slot that holds unlanded work ([#104](https://github.com/kunchenguid/treehouse/issues/104)) ([04d8725](https://github.com/kunchenguid/treehouse/commit/04d87252f918dc3942318817b74413bf55f5b3eb))
* **process:** wait for SIGKILLed processes to be reaped before return runs git ([#102](https://github.com/kunchenguid/treehouse/issues/102)) ([664adf8](https://github.com/kunchenguid/treehouse/commit/664adf81e4a427080449aa8e4b76b53cc54f8a24))

## [2.2.1](https://github.com/kunchenguid/treehouse/compare/v2.2.0...v2.2.1) (2026-08-21)


### Bug Fixes

* **return:** refuse to reset a worktree that still has live writers ([#103](https://github.com/kunchenguid/treehouse/issues/103)) ([978da87](https://github.com/kunchenguid/treehouse/commit/978da8750da4f6faebbef90ccdb23aaac6211118))

## [2.2.0](https://github.com/kunchenguid/treehouse/compare/v2.1.1...v2.2.0) (2026-08-19)


### Features

* add --root flag and TREEHOUSE_ROOT env for the worktree root ([#93](https://github.com/kunchenguid/treehouse/issues/93)) ([5e3d282](https://github.com/kunchenguid/treehouse/commit/5e3d282592dfef5e60a5027797aa917f08c6cbf0))
* add no-fetch worktree acquisition ([164d903](https://github.com/kunchenguid/treehouse/commit/164d9036569a406d664f988f064c6a58eea1a645))


### Bug Fixes

* **cmd:** resolve main repo root for pool commands run inside a worktree ([#51](https://github.com/kunchenguid/treehouse/issues/51)) ([3fcd637](https://github.com/kunchenguid/treehouse/commit/3fcd63771a6368fa357a9a4079a9b6e242202dcb))
* detect squash-merged worktrees ([#88](https://github.com/kunchenguid/treehouse/issues/88)) ([a651776](https://github.com/kunchenguid/treehouse/commit/a651776a47a2911d260c55472ccdfc5f6a3aeaf8))
* ignore in-project pool via .git/info/exclude ([fdb3f99](https://github.com/kunchenguid/treehouse/commit/fdb3f99ba1c7c6d24db7efbcbb569a61f6535489))
* **pool:** prune stale worktree registrations before adding in get ([844acc4](https://github.com/kunchenguid/treehouse/commit/844acc4d1d7d8078f1110295689d94853a921dd7)), closes [#31](https://github.com/kunchenguid/treehouse/issues/31)

## [2.1.1](https://github.com/kunchenguid/treehouse/compare/v2.1.0...v2.1.1) (2026-07-31)


### Bug Fixes

* **ci:** suppress pull_request runs on release-please PRs ([#77](https://github.com/kunchenguid/treehouse/issues/77)) ([da7eda2](https://github.com/kunchenguid/treehouse/commit/da7eda26e5f26e0a1bf87a0d67e7553d72952cdf))

## [2.1.0](https://github.com/kunchenguid/treehouse/compare/v2.0.1...v2.1.0) (2026-07-20)


### Features

* **pool:** add stable lease identities ([#68](https://github.com/kunchenguid/treehouse/issues/68)) ([e914cca](https://github.com/kunchenguid/treehouse/commit/e914cca93693be4c47e0a4df1bf7439afd5e820a))

## [2.0.1](https://github.com/kunchenguid/treehouse/compare/v2.0.0...v2.0.1) (2026-07-14)


### Bug Fixes

* **pool:** make state persistence atomic and recoverable ([#55](https://github.com/kunchenguid/treehouse/issues/55)) ([c76015d](https://github.com/kunchenguid/treehouse/commit/c76015d914e8ae7068c024c68c58860e10e8ee52))

## [2.0.0](https://github.com/kunchenguid/treehouse/compare/v1.8.0...v2.0.0) (2026-06-24)


### ⚠ BREAKING CHANGES

* **cmd:** the `treehouse destroy --force` flag is removed. Replace it with the specific --include-unlanded / --include-in-use / --include-leased flag(s) for the risk you intend to override, plus --yes, and pass an explicit pool path to --all.

### Features

* **cmd:** make destroy safe by default ([#37](https://github.com/kunchenguid/treehouse/issues/37)) ([0190382](https://github.com/kunchenguid/treehouse/commit/0190382c6f3b95025667b5b01e688e779bf3c516))

## [1.8.0](https://github.com/kunchenguid/treehouse/compare/v1.7.0...v1.8.0) (2026-06-22)


### Features

* **pool:** add durable worktree leases ([#35](https://github.com/kunchenguid/treehouse/issues/35)) ([97d6708](https://github.com/kunchenguid/treehouse/commit/97d67089ea55cba166c3f4d5332e9a7a09206057))

## [1.7.0](https://github.com/kunchenguid/treehouse/compare/v1.6.0...v1.7.0) (2026-06-20)


### Features

* **pool:** classify orphaned worktrees during prune ([#28](https://github.com/kunchenguid/treehouse/issues/28)) ([836044f](https://github.com/kunchenguid/treehouse/commit/836044f85e992d2fd65969dca387704998c144b6))

## [1.6.0](https://github.com/kunchenguid/treehouse/compare/v1.5.0...v1.6.0) (2026-06-20)


### Features

* **cmd:** add global prune mode ([#26](https://github.com/kunchenguid/treehouse/issues/26)) ([6de3a91](https://github.com/kunchenguid/treehouse/commit/6de3a9150453cc5cf5fb4e95627788551adae66c))

## [1.5.0](https://github.com/kunchenguid/treehouse/compare/v1.4.0...v1.5.0) (2026-06-19)


### Features

* **prune:** add safe stale worktree pruning ([#24](https://github.com/kunchenguid/treehouse/issues/24)) ([3395c20](https://github.com/kunchenguid/treehouse/commit/3395c20e41dbb563e3437c4a0a5e031ce042ca2a))

## [1.4.0](https://github.com/kunchenguid/treehouse/compare/v1.3.2...v1.4.0) (2026-05-15)


### Features

* **pool:** add user lifecycle hooks ([#22](https://github.com/kunchenguid/treehouse/issues/22)) ([9c70d0b](https://github.com/kunchenguid/treehouse/commit/9c70d0b73c6ca1c1783828f3e9d215612993a3b4))

## [1.3.2](https://github.com/kunchenguid/treehouse/compare/v1.3.1...v1.3.2) (2026-05-02)


### Bug Fixes

* **cmd:** detach worktrees before pool reuse ([#19](https://github.com/kunchenguid/treehouse/issues/19)) ([0d849a3](https://github.com/kunchenguid/treehouse/commit/0d849a3b82a8647f507b1e2f186dc041c930fe35))

## [1.3.1](https://github.com/kunchenguid/treehouse/compare/v1.3.0...v1.3.1) (2026-04-16)


### Bug Fixes

* **process:** safely clean up lingering worktree processes ([#17](https://github.com/kunchenguid/treehouse/issues/17)) ([c1e443d](https://github.com/kunchenguid/treehouse/commit/c1e443de639d3bf5a867e71f218153c4816c78ef))

## [1.3.0](https://github.com/kunchenguid/treehouse/compare/v1.2.1...v1.3.0) (2026-04-04)


### Features

* **nix:** add flake.nix and flake.lock ([#15](https://github.com/kunchenguid/treehouse/issues/15)) ([500d2f9](https://github.com/kunchenguid/treehouse/commit/500d2f9e26429d02e8378142556af8ad9be8cbd0))


### Bug Fixes

* update vendor hash handling in workflow ([fe692a5](https://github.com/kunchenguid/treehouse/commit/fe692a5fdce020a003581abece3d7eacf88dfb03))

## [1.2.1](https://github.com/kunchenguid/treehouse/compare/v1.2.0...v1.2.1) (2026-03-21)


### Bug Fixes

* use remote URL for pool hash for local repos ([7b13a4d](https://github.com/kunchenguid/treehouse/commit/7b13a4dd52dbef7270cd1535575e1a0610d8d296))

## [1.2.0](https://github.com/kunchenguid/treehouse/compare/v1.1.5...v1.2.0) (2026-03-17)


### Features

* **config:** add configurable root for pool directory ([#12](https://github.com/kunchenguid/treehouse/issues/12)) ([0bc1378](https://github.com/kunchenguid/treehouse/commit/0bc1378b758ac93bb4ca430a942e87a5c3b8f020))

## [1.1.5](https://github.com/kunchenguid/treehouse/compare/v1.1.4...v1.1.5) (2026-03-16)


### Bug Fixes

* update repository URLs ([b9d1fda](https://github.com/kunchenguid/treehouse/commit/b9d1fda8f919411002e8d5119e35693e7a97fbbe))

## [1.1.4](https://github.com/kunchenguid/treehouse/compare/v1.1.3...v1.1.4) (2026-03-15)


### Bug Fixes

* app update permission error ([0559e99](https://github.com/kunchenguid/treehouse/commit/0559e99680c8d1f0a99f969c9fdf5407e4027aa3))

## [1.1.3](https://github.com/kunchenguid/treehouse/compare/v1.1.2...v1.1.3) (2026-03-15)


### Bug Fixes

* recheck app update when cached version is stale ([21d93e2](https://github.com/kunchenguid/treehouse/commit/21d93e2e36eb3948623e21a6e92c520bae476da9))

## [1.1.2](https://github.com/kunchenguid/treehouse/compare/v1.1.1...v1.1.2) (2026-03-15)


### Bug Fixes

* shorter version display ([9c51b35](https://github.com/kunchenguid/treehouse/commit/9c51b35fdb34cc1230d14c6695cd32f04345cf9b))

## [1.1.1](https://github.com/kunchenguid/treehouse/compare/v1.1.0...v1.1.1) (2026-03-15)


### Bug Fixes

* install under ~/.local/bin when in PATH ([08bb5b6](https://github.com/kunchenguid/treehouse/commit/08bb5b6ec2fa91d2f9e426164cd3313d90812918))

## [1.1.0](https://github.com/kunchenguid/treehouse/compare/v1.0.2...v1.1.0) (2026-03-15)


### Features

* **status:** show current worktree status ([75b24a0](https://github.com/kunchenguid/treehouse/commit/75b24a0b8a0fe2ea4ed88e8a28288c529403e951))
* use latest default branch for worktree ([df3ee7b](https://github.com/kunchenguid/treehouse/commit/df3ee7b364aab64e1d7099422815ebeb43dc6c58))

## [1.0.2](https://github.com/kunchenguid/treehouse/compare/v1.0.1...v1.0.2) (2026-03-15)


### Bug Fixes

* **cli:** expose version flag and set rootCmd.Version ([ac84c4a](https://github.com/kunchenguid/treehouse/commit/ac84c4a38c72b75a9fe633e138b50aaf66d20e26))
* windows test failure ([4e24e5f](https://github.com/kunchenguid/treehouse/commit/4e24e5ff502e502f657bb417ea74a44012a28eb8))

## [1.0.1](https://github.com/kunchenguid/treehouse/compare/v1.0.0...v1.0.1) (2026-03-14)


### Bug Fixes

* CI failures ([d744564](https://github.com/kunchenguid/treehouse/commit/d744564529cad1975c78a29b2b8ed4d61d529977))

## 1.0.0 (2026-03-14)


### Features

* initial project setup ([bfc295d](https://github.com/kunchenguid/treehouse/commit/bfc295dd52e0452b5a69ea2642864449380d54b5))
