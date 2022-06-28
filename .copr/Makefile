rpmbuild_src = $(shell dirname $(spec))
.PHONY: prepare srpm rpm

prepare:
	dnf -y install rpmdevtools rpm-build fedpkg
	fedpkg --name kernel sources
	spectool -g --directory $(rpmbuild_src) $(spec)

srpm: prepare
	rpmbuild -bs --define "_sourcedir $(rpmbuild_src)" --define "_srcrpmdir $(outdir)" $(spec)

rpm: prepare
	rpmbuild -bb --define "_sourcedir $(rpmbuild_src)" --define "_rpmdir $(outdir)" $(spec)
