VERSION = 0.1

image:
	docker build -t "gcr.io/jetstack-build-infra/cert-manager-golang:$(VERSION)" .

push: image
	gcloud docker -- push "gcr.io/jetstack-build-infra/cert-manager-golang:$(VERSION)"

.PHONY: image push
